# DA-Tool

The tool described below is used to analyze data from a csv format file, in which
there is a column named “group” and columns have a clear division into parametric and
non-parametric data.

    Tool launch - instructions
    1.1 It is mandatory to have the R language installed on the device running the tool and
    access to the internet. If R is not installed, it should be downloaded from:
    https://cran.r-project.org/.
    1.2 To create a summary report in html extension, it is necessary to have the pandoc application, which can be downloaded from
    https://pandoc.org/installing.html.
    1.2.1 After installing Pandoc, make sure it is available in the PATH environment variable. This can be checked in the command line by typing pandoc --version
    1.2.2 If the Pandoc executable is not available in the PATH environment variable,
    it must be added to it, so that R and RStudio can locate it. Here's how to do it in
    Windows: Right-click on "My Computer" or "This PC" and select "Properties" -> "Advanced system settings" -> "Environment Variables". In the "System Variables" section, find the "PATH" or "Path" variable and click
    "Edit". Add the path to the directory where the Pandoc executable is located
    (the path should end with a semicolon). Finally, click "OK" and close
    all windows.
    1.3 Then run the Windows command line.
    1.3.1 By typing “command line” in the system search box on the left side.
    1.3.2 By using the windows + r keyboard shortcut.
    1.4 Enter the command: cd “path to the directory where the input argument and R script are located”.
    Example: cd C:\Users\marta\OneDrive\Documents\DA_project
    1.5 Then enter the command:
    "C:\Program Files\R\R-4.2.3\bin\R.exe" CMD BATCH --vanilla --slave "--args
    exampleData-Project(3).csv" data_analysis.R
    *blue markings indicate a possible need to adjust paths:
    *R-4.2.3 - entering the correct version of the R language present on the device,
    *exampleData-Project(3) - specifying the correct name of the input argument in
    the csv format on which the analysis will be conducted.
    1.6 In the working directory (after about 330 seconds) a complete file named
    data_analysis.Rout appears, containing a report of all conducted tests
    along with a summary report in html format.
    
    Tool operation scheme
    1.Loading the input argument provided by the user from the command line, in its absence, stopping the program along with an information message.
    2.Reading data for analysis from a csv file (indicated by the argument).
    3.Handling missing data. Finding missing values in the data, replacing them
    with the median (resistant to outliers) of the group parameter, and displaying a report of where and what changes occurred.
    4.Visualization of outliers and additionally the general distribution of data using
    box plots. Each plot consists of a single, considered numerical parameter and its values in each group. All plots have been saved to a .png file, under the name "boxplot_" + column name.
    5.Displaying all outliers in a given parameter divided by group.
    6.Presenting in a table and saving to a csv file conducted characteristics:
    average, standard deviation, median, kurtosis, skewness, and range, for each
    parameter with numerical variables in the group.
    7.Performing a test for conformity with the normal distribution and visualizing this phenomenon
    through density plots conducted for each parameter value in all
    groups. All plots have been saved in the working directory under the name
    "Density_plot_for_" + parameter name in png format.
    8.Conducting a test for homogeneity of variances.
    9.Collecting results of the above two tests to analyze differences between
    groups according to the table.
    10.Displaying the occurrence or absence of differences between groups with respect to the adopted
    classificatory value p.value resulting from conducted statistical tests.
    11.Visualization in the form of a bar chart and conducting a chi-sq test for non-numerical parameters.
    12.Performing a correlation analysis using Pearson's method for parameters consistent with
    the normal distribution. However, for parameters not consistent with the normal distribution,
    Spearman's method is used to minimize the probability of detecting
    correlation between parameters deviating from the normal data distribution.
    Visualization of correlations between two analyzed parameters in all
    groups.
    Returning a report relating to, among others, the tool's operation time, as well as
    a self-rendering report in html format.
    
    3.Interpretation of returned results
    All the below results are found in the directory where
    the commands from the tool's instruction manual were executed.
    1.data_analysis.Rout
    This file contains a report of conducted tests and results for batch mode.
    2.Boxplots
    Boxplots were mainly used to retrieve and subsequently report outlier values
    (marked with a white dot), which in such charts are determined using the interquartile range (IQR). However, boxplots undoubtedly also illustrate
    other significant features of the data such as: median, interquartile range, range, first
    quartile, third quartile, maximum, and minimum of non-outlying values. On the Y-axis are
    the values of the considered parameter, and on the X-axis which group it pertains to.
    3.Characteristics - csv file
    All collected characteristics have been grouped together in a csv file as seen
    below. Each column name appears as many times as there are analyzed groups and together with
    it measurements. Characteristics are calculated not with respect to the entire column of parameters but to the
    values of parameters in a specific group.
    
    The most significant characteristics for analysis were adopted as follows.
    1.Average - the most commonly used measure of central tendency. Sensitive to outliers.
    Useful for summarizing a set of data with one value.
    Standard deviation - is a measure of the dispersion or variability of data around the average.
    2.Median - a measure of central tendency that is resistant to outliers. In
    situations where data have extreme values, the median is often more representative than
    the average.
    3.Kurtosis - refers to the "thickness" of the tails of the distribution and is a measure of the concentration of
    outliers in a given distribution.
    4.Skewness - measures the asymmetry of the distribution of data around the average value.
    5.Range - the difference between the highest and lowest value in a data set. It provides a general
    idea about the spread of the data, but is very sensitive to outliers.
    
    4.Density plots
    Density plots were used to visualize the conformity or lack thereof of the analyzed values in
    the group column with the normal distribution, characterized by a bell shape. On the OY axis are
    densities, and on the OX axis are the measurement values of a given column divided by
    groups.
    5.Barplot
    The bar chart was used to visualize non-numerical parameters. In
    the tool's program, hard coding of gender was abandoned to limit it only to
    the group parameter. In the legend, there will be a designation equivalent to that
    found in the input file (without further elaboration of the actual logic in
    the case of gender). P value visible in the upper left corner is the result of the chi-sq test
    created for the analysis of non-numerical parameters.
    6.Correlations
    Correlation analyses were conducted between all parameters of each group.
    On the OY axis is the value of one compared parameter, on the OX axis the other. In
    the upper left corner are visible two results returned by the correlation test: p.value and the value
    of the R factor. The legend explains which visualization illustrates the result of the correlation in a given group.
    
    7.Report
    The summary report was included in this project due to its universality.
    Almost any device with an internet browser can display HTML documents,
    making reports in this format easy to share and review by different
    people, regardless of whether they have the R software installed.
