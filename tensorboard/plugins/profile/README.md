# The Profile Plugin Dashboard

## JSON format for the Overview Page and the Input-pipeline Analyzer

The Overview Page and Input-pipeline analyzer are ported from Google internal
tools where google-chart is used extensively. The original consumer for this
JSON format is
[google.visualization.DataTable](https://developers.google.com/chart/interactive/docs/reference#DataTable).
We are in a process of moving from google-chart to Plottable and other
visualization tools provided by Tensorboard.

### 1. JSON format for the Overview Page

JSON for the Overview Page includes four seperate DataTables described below.
Each table may have some properties, or some tabular data, or both.

#### 1.1 Performance Summary DataTable

1.1.1 Properties:

*   matrix_unit_utilization_percent
*   device_idle_time_percent
*   host_idle_time_percent

1.1.2 Tabular data: rows are TensorFlow operations. Column ids are defined
below.

*   self_time_fraction: number
*   cumulative_time_fraction: number
*   category: string
*   name: string
*   flop_rate: number

#### 1.2 Device Step-time DataTable

1.2.1 Properties:

*   infeed_percent_average
*   infeed_percent_maximum
*   infeed_percent_minimum
*   infeed_percent_standard_deviation
*   steptime_ms_average
*   steptime_ms_maximum
*   steptime_ms_minimum
*   steptime_ms_standard_deviation
*   summary_color
*   summary_text

1.2.2 Tabular data: rows are training steps. Column ids are defined below.

*   stepnum: string
*   noninfeedTimeMs: number
*   infeedTimeMs: number
*   tooltip: string (NOT USED)
*   infeedPercentAverage: number
*   infeedPercentMin: number
*   infeedPercentMax: number

#### 1.3 Run-environment DataTable

1.3.1 Properties:

*   host_count
*   tpu_type
*   tpu_core_count
*   batch_size
*   change_list
*   build_time
*   build_target

1.3.2 Tabular data: rows are hosts. Column ids are defined below.

*   host_id: string
*   command_line: string
*   start_time: string

#### 1.4 Recommendation DataTable

1.4.1 Properties:

*   bottleneck
*   statement

1.4.2 Tabular data: rows are recommendations. Column ids are defined below.

*   tip_type: string
*   link: string

### 2. JSON format for the Input-pipeline Analyzer

JSON for the Input-pipeline Analyzer uses two separate DataTables: the first
DataTable contains statistics for device step time; the second DataTable
contains statistics for host side state. Each DataTable is associated with some
table properties and some tabular data.

#### 2.1. Device Step-time DataTable

The same as the one described in Section 1.2.

#### 2.2 Host Side DataTable

2.2.1 Properties:

*   advanced_file_read_us
*   conclusion
*   demanded_file_read_us
*   enqueue_us
*   preprocessing_us

2.2.2 Tabular data: rows are input-pipeline related tensorflow ops. column ids
are defined below.

*   opName: string
*   count: number
*   timeInMs: number
*   timeInPercent: number
*   selfTimeInMs: number
*   selfTimeInPercent: number
*   category: string
