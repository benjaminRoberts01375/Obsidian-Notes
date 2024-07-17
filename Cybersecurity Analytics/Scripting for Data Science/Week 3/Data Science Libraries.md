<table>
<tr>
<td>Library Name</td>
<td>Advantages</td>
<td>Disadvantages</td>
<td>Usage</td>
</tr>
<tr>
<td>TensorFlow</td>
<td>
<ol>
<li>Ease of entry: TensorFlow has multiple levels of abstraction available, which allows people new to the API to start off somewhat easy, and progressively perform deeper and more involved operations <i>API Documentation | TensorFlow v2.16.1</i>, 2024).</li>
<li>Support for Java (though depreciated), JavaScript, Python, and C++ with strong documentation for each language <i>API Documentation | TensorFlow v2.16.1</i>, 2024)</li>
</ol>
</td>
<td>
<ol>
<li>Limited GPU support: While TensorFlow supports CPU compute, GPU support is natively limited to NVIDIA GeeksforGeeks, 2022). Though this is mitigated by Apple's tensorflow-metal plug-in Apple Inc., n.d.).</li>
<li>Performance: Due to TensorFlow's age, TensorFlow finds itself needing to support old APIs that are now redundant. However, these older APIs do limit TensorFlow's ability to simplify its codebase.</li>
</ol>
</td>
<td>
<p>TensorFlow is used for researching and training machine learning models across a range of different programming languages and devices.</p>
<p>For example, a team and I built a machine learning model to predict if your StackOverflow question was likely going to be answered based on statistics like number of code blocks and word count.</p>
</td>
</tr>
<tr>
<td>Pandas</td>
<td>
<ol>
<li>Documentation: Pandas having been a long-standing library has considerable community documentation, as well as first party documentation for new comers, user, API in the form of definitions, examples, and explanations.</li>
<li>Numpy: Support for NumPy is built-in, even supporting NumPy 2.0 two months before its release <i>Getting Started &mdash; Pandas 2.2.2 Documentation</i>, 2024).&nbsp;</li>
</ol>
</td>
<td>
<ol>
<li>Memory Efficiency: Pandas is known for its poor memory performance, forcing developers to optimize memory by loading large datasets in chunks GeeksforGeeks, 2021)</li>
<li>Reliance on NumPy: Pandas is not self contained, rather relying on NumPy, which can slightly complicate application dependencies.</li>
</ol>
</td>
<td>
<p>Pandas is used for data visualization and formatting, primarily 2D tables. Pandas is able to use code for manipulating and coloring this data, as well as creating graphs.</p>
<p>For example, Pandas can be used to display data about the stock market, changing the line color from blue (historical) to red (prediction) to allow typical users to asses results.</p>
</td>
</tr>
<tr>
<td>Seaborn</td>
<td>
<ol>
<li>Matplotlib: Support for Matplotlib is built-in, allowing for static, interactive, and animated charts and graphics (Matplotlib).</li>
<li>Jupyter notebook documentation: Jupyter notebooks, a data science program allowing the user to segment code into cells for easy caching of results, has support from Seaborn for improved analysis support <i>User Guide and Tutorial &mdash; Seaborn 0.13.2 Documentation</i>, 2024).</li>
</ol>
</td>
<td>
<ol>
<li>Due to the nature of Seaborn being a wrapper around Matplotlib, it can be difficult to have granular control over visualizations.</li>
<li>Due to Seaborn being based around Matplotlib, it suffers many of the same high memory issues Matplotlib does with larger datasets.</li>
</ol>
</td>
<td>
<p>Seaborn is built on Matplotlib, and attempts to make visualizations easier by having templates, and simpler syntax. Additionally, Seaborn integrates with Pandas to meet data scientists where they likely are.</p>
<p>An example of how Seaborn could be used is to generate a heat map for where customers are located that connect to a service, allowing infrastructure teams to better optimize where data centers are.</p>
</td>
</tr>
</table>

<p>References</p>
<div>
<p><i>API Documentation | TensorFlow v2.16.1</i>. (2024, April 26). TensorFlow. Retrieved July 16, 2024, from <span class="url">https://www.tensorflow.org/api_docs</span></p>
<p>Apple Inc. (n.d.). <i>TensorFlow Plugin - Metal - Apple Developer</i>. Apple Developer. Retrieved July 16, 2024, from <span class="url">https://developer.apple.com/metal/tensorflow-plugin/</span></p>
<p>GeeksforGeeks. (2021, April 30). <i>Bypassing pandas memory limitations</i>. Retrieved July 16, 2024, from <span class="url">https://www.geeksforgeeks.org/bypassing-pandas-memory-limitations</span></p>
<p>GeeksforGeeks. (2022, February 28). <i>Advantages and Disadvantages of TensorFlow</i>. Retrieved July 16, 2024, from <span class="url">https://www.geeksforgeeks.org/advantages-and-disadvantages-of-tensorflow</span></p>
<p><i>Getting started &mdash; pandas 2.2.2 documentation</i>. (2024). Pandas. Retrieved July 16, 2024, from <span class="url">https://pandas.pydata.org/docs/getting_started/index.html#getting-started</span></p>
<p><i>User guide and tutorial &mdash; seaborn 0.13.2 documentation</i>. (2024). Retrieved July 16, 2024, from <span class="url">https://seaborn.pydata.org/tutorial.html</span></p>
<p><i>Visualization with Python</i>. (n.d.). Matplotlib. Retrieved July 16, 2024, from <span class="url">https://matplotlib.org/</span></p>
</div>