# Monitors NVIDIA GPU information and log the data into a pandas DataFrame - Windows only.

## pip install nvidiacheck 

#### Tested against Windows 10 / Python 3.10 / Anaconda 



```python

        Parameters:
            savepath (str, optional): The file path to save the log data as a CSV file.
                                      If provided, the data will be saved upon KeyboardInterrupt.
            sleeptime (int, optional): The time interval (in seconds) between each data logging.

        Returns:
            pandas.DataFrame: A DataFrame containing the logged NVIDIA GPU information with the following columns:
                - index: GPU index.
                - name: GPU name.
                - memory.total [MiB]: Total GPU memory in MiB (Mebibytes).
                - memory.used [MiB]: Used GPU memory in MiB (Mebibytes).
                - memory.free [MiB]: Free GPU memory in MiB (Mebibytes).
                - temperature.gpu: GPU temperature in Celsius.
                - pstate: GPU performance state.
                - utilization.gpu [%]: GPU utilization percentage.
                - utilization.memory [%]: Memory utilization percentage.
                - timestamp: Timestamp in the format "YYYY_MM_DD_HH_MM_SS".

        Description:
            This function uses the NVIDIA System Management Interface (nvidia-smi) to query GPU information,
            including memory usage, temperature, performance state, and utilization. The data is collected
            in real-time and logged into a pandas DataFrame. The logging continues indefinitely until a
            KeyboardInterrupt (usually triggered by pressing Ctrl + C).

            If the 'savepath' parameter is provided, the collected GPU information will be saved to a CSV
            file when the monitoring is interrupted by the user (KeyboardInterrupt).

            Note: This function is intended for systems with NVIDIA GPUs on Windows and requires the nvidia-smi.exe
            executable to be available in the system path.

        Example:
            from nvidiacheck import nvidia_log
            # Start monitoring NVIDIA GPU and display the real-time log
            nvidia_log()

            # Start monitoring NVIDIA GPU and save the log data to a CSV file
            nvidia_log(savepath="gpu_log.csv")

            # Start monitoring NVIDIA GPU with a custom time interval between logs (e.g., 2 seconds)
            nvidia_log(sleeptime=2)

              index                            name  memory.total [MiB]  memory.used [MiB]  memory.free [MiB]  temperature.gpu  pstate  utilization.gpu [%]  utilization.memory [%]            timestamp
    0     0   NVIDIA GeForce RTX 2060 SUPER            8192 MiB           1321 MiB           6697 MiB               45      P8                 16 %                     5 %  2023_07_18_11_52_55
      index                            name  memory.total [MiB]  memory.used [MiB]  memory.free [MiB]  temperature.gpu  pstate  utilization.gpu [%]  utilization.memory [%]            timestamp
    1     0   NVIDIA GeForce RTX 2060 SUPER            8192 MiB           1321 MiB           6697 MiB               44      P8                 17 %                     6 %  2023_07_18_11_52_56
      index                            name  memory.total [MiB]  memory.used [MiB]  memory.free [MiB]  temperature.gpu  pstate  utilization.gpu [%]  utilization.memory [%]            timestamp
    2     0   NVIDIA GeForce RTX 2060 SUPER            8192 MiB           1321 MiB           6697 MiB               44      P8                  2 %                     4 %  2023_07_18_11_52_57
      index                            name  memory.total [MiB]  memory.used [MiB]  memory.free [MiB]  temperature.gpu  pstate  utilization.gpu [%]  utilization.memory [%]            timestamp
    3     0   NVIDIA GeForce RTX 2060 SUPER            8192 MiB           1321 MiB           6697 MiB               44      P8                  4 %                     5 %  2023_07_18_11_52_58
      index                            name  memory.total [MiB]  memory.used [MiB]  memory.free [MiB]  temperature.gpu  pstate  utilization.gpu [%]  utilization.memory [%]            timestamp
    4     0   NVIDIA GeForce RTX 2060 SUPER            8192 MiB           1321 MiB           6697 MiB               46      P2                 22 %                     1 %  2023_07_18_11_52_59
      index                            name  memory.total [MiB]  memory.used [MiB]  memory.free [MiB]  temperature.gpu  pstate  utilization.gpu [%]  utilization.memory [%]            timestamp
    5     0   NVIDIA GeForce RTX 2060 SUPER            8192 MiB           1320 MiB           6698 MiB               45      P8                  0 %                     0 %  2023_07_18_11_53_00
      index                            name  memory.total [MiB]  memory.used [MiB]  memory.free [MiB]  temperature.gpu  pstate  utilization.gpu [%]  utilization.memory [%]            timestamp
    6     0   NVIDIA GeForce RTX 2060 SUPER            8192 MiB           1320 MiB           6698 MiB               45      P8                  2 %                     4 %  2023_07_18_11_53_01
      index                            name  memory.total [MiB]  memory.used [MiB]  memory.free [MiB]  temperature.gpu  pstate  utilization.gpu [%]  utilization.memory [%]            timestamp
    7     0   NVIDIA GeForce RTX 2060 SUPER            8192 MiB           1320 MiB           6698 MiB               44      P8                 12 %                     5 %  2023_07_18_11_53_02
      index                            name  memory.total [MiB]  memory.used [MiB]  memory.free [MiB]  temperature.gpu  pstate  utilization.gpu [%]  utilization.memory [%]            timestamp
    8     0   NVIDIA GeForce RTX 2060 SUPER            8192 MiB           1320 MiB           6698 MiB               44      P8                  3 %                     4 %  2023_07_18_11_53_03
   
```