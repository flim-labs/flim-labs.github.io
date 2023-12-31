

<a name="readme-top"></a>

<div align="center">
  <h1>Intensity Tracing - File Format </h1>
</div>
<div align="center">
  <a href="https://www.flimlabs.com/">
    <img src="../../assets/flimlabs-logo.png" alt="Logo" width="120" height="120">
  </a>
</div>
<br>




<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#introduction">Introduction</a>
    </li>
    <li><a href="#file-format">File Format</a></li>
    <li><a href="#data-visualization">Data visualization</a></li>
    <li><a href="#useful-links">Useful links</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>



## Introduction

The [Intensity Tracing](https://github.com/flim-labs/intensity-tracing-py) tool allows seamless export of photons counts analyzed data to binary files, with convenient plotting and visualization capabilities. This guide provides an in-depth exploration of the **binary file structure**, offering a comprehensive understanding of how exported data is formatted and can be leveraged.

<p align="right">(<a href="#readme-top">back to top</a>)</p>




## File Format

<div align="center">
    <img src="../../assets/exported-data-visualization.png" alt="GUI" width="100%">
</div>

To plot and visualize previously exported raw data (with GUI or console mode)  you can launch the```plot_data_file.py``` script. 
This script reads binary data from the local saved file and utilizes the ```matplotlib``` library to visualize photons intensity informations.

Here a detailed explanation of the exported binary data file structure:

##### Header (4 bytes):
The first 4 bytes of the file must be ```IT01```. This serves as a validation check to ensure the correct format of the file. If the check fails, the script prints "Invalid data file" and exits.

##### Metadata Section (Variable length):
Following the header, metadata is stored in the file. This includes:
- ```JSON length (4 bytes)```: an unsigned integer representing the length of the JSON metadata.
- ```JSON metadata```: this is a variable-length string that contains information about the data, including _enabled channels_, _bin width_, _acquisition time_, and _laser period_. This information is printed to the console.

##### Data Records (40 bytes each):

After the metadata, the script enters a loop to read and process data in chunks of 40 bytes. Each chunk represents a data record containing:
- ```Timestamp (8 bytes)```: A double representing the photons' data acquisition time in milliseconds.
- ```Channel Values (32 bytes)```: 8 unsigned integers (4 bytes each) representing photon counts for each channel at the corresponding timestamp.

<p align="right">(<a href="#readme-top">back to top</a>)</p>


## Data Visualization

To visualize/plot your saved data, replace ```file_path``` value with the local path of your file:

```file_path = 'INSERT DATA FILE PATH HERE'```

You can find your file at this path:

```C:\Users\YOUR_USER\.flim-labs\data```


<p align="right">(<a href="#readme-top">back to top</a>)</p>


## Useful Links

For more details about the project follow these links:

- [Intensity Tracing introduction](../intensity-tracing/index.md)
- [Intensity Tracing GUI guide](../intensity-tracing/v1.0/index.md)
- [Intensity Tracing Console guide ](./intensity-tracing-console.md)


<p align="right">(<a href="#readme-top">back to top</a>)</p>




## License

Distributed under the MIT License.

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- CONTACT -->
## Contact

FLIM LABS: info@flimlabs.com

Project Link: [FLIM LABS - Intensity Tracing](https://github.com/flim-labs/intensity-tracing-py)

<p align="right">(<a href="#readme-top">back to top</a>)</p>




