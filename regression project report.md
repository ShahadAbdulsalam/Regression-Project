# Report 

## First: Web scraping steps.

### 1- Import URL & use driver to get the page.



```python
url = "https://coinmarketcap.com/currencies/solana/historical-data/"

```


```python

driver = webdriver.Chrome(r'C:\Users\sshah\.wdm\drivers\chromedriver\win32\94.0.4606.61\chromedriver.exe')

```


```python
driver.get(url)
```

### 2- Use Selenium to click on the buttuns & beautifulsoup to find rows by the tags.


```python
data_find= driver.find_element_by_xpath('//*[@id="__next"]/div/div[1]/div[2]/div/div[3]/div/div/div[2]')
```


```python
page = data_find.get_attribute('innerHTML')
```


```python
buttun1 = driver.find_element_by_xpath('//*[@id="__next"]/div/div[1]/div[2]/div/div[3]/div/div/p[1]/button')
buttun1.click()
```


```python
soup=BeautifulSoup(page, 'html5lib')
```


```python
rows = soup.find_all('tr')
rows
```




    [<tr><th class="stickyTop" style="text-align: left; top: 64px;">Date</th><th class="stickyTop" style="top: 64px;">Open*</th><th class="stickyTop" style="top: 64px;">High</th><th class="stickyTop" style="top: 64px;">Low</th><th class="stickyTop" style="top: 64px;">Close**</th><th class="stickyTop" style="top: 64px;">Volume</th><th class="stickyTop" style="text-align: right; top: 64px;">Market Cap</th></tr>,
     <tr><td style="text-align: left;">Oct 18, 2021</td><td>$160.00</td><td>$162.86</td><td>$155.03</td><td>$157.23</td><td>$1,698,878,759</td><td style="text-align: right;">$47,254,003,672</td></tr>,
     <tr><td style="text-align: left;">Oct 17, 2021</td><td>$157.46</td><td>$167.43</td><td>$154.09</td><td>$159.74</td><td>$2,168,838,138</td><td style="text-align: right;">$47,991,515,200</td></tr>,
     <tr><td style="text-align: left;">Oct 16, 2021</td><td>$163.01</td><td>$164.71</td><td>$156.74</td><td>$157.54</td><td>$1,531,502,795</td><td style="text-align: right;">$47,304,541,727</td></tr>,
     <tr><td style="text-align: left;">Oct 15, 2021</td><td>$150.05</td><td>$165.12</td><td>$146.98</td><td>$162.60</td><td>$3,970,589,003</td><td style="text-align: right;">$48,823,235,028</td></tr>,
     <tr><td style="text-align: left;">Oct 14, 2021</td><td>$148.02</td><td>$155.33</td><td>$147.33</td><td>$149.76</td><td>$1,948,101,208</td><td style="text-align: right;">$44,950,465,986</td></tr>,
     <tr><td style="text-align: left;">Oct 13, 2021</td><td>$152.52</td><td>$155.35</td><td>$144.41</td><td>$148.18</td><td>$2,105,226,551</td><td style="text-align: right;">$44,438,380,256</td></tr>,
     <tr><td style="text-align: left;">Oct 12, 2021</td><td>$145.01</td><td>$153.26</td><td>$137.81</td><td>$152.74</td><td>$2,853,992,440</td><td style="text-align: right;">$45,806,350,192</td></tr>,
     <tr><td style="text-align: left;">Oct 11, 2021</td><td>$147.80</td><td>$153.92</td><td>$140.36</td><td>$144.86</td><td>$1,851,795,187</td><td style="text-align: right;">$43,418,344,986</td></tr>,
     <tr><td style="text-align: left;">Oct 10, 2021</td><td>$156.75</td><td>$158.36</td><td>$146.90</td><td>$148.05</td><td>$1,556,965,341</td><td style="text-align: right;">$44,350,090,749</td></tr>,
     <tr><td style="text-align: left;">Oct 09, 2021</td><td>$158.70</td><td>$161.41</td><td>$154.87</td><td>$156.83</td><td>$1,522,023,824</td><td style="text-align: right;">$46,957,713,350</td></tr>,
     <tr><td style="text-align: left;">Oct 08, 2021</td><td>$154.26</td><td>$168.85</td><td>$152.76</td><td>$158.95</td><td>$2,781,848,650</td><td style="text-align: right;">$47,593,592,988</td></tr>,
     <tr><td style="text-align: left;">Oct 07, 2021</td><td>$153.96</td><td>$161.36</td><td>$150.54</td><td>$154.28</td><td>$2,579,187,256</td><td style="text-align: right;">$45,995,023,049</td></tr>,
     <tr><td style="text-align: left;">Oct 06, 2021</td><td>$164.61</td><td>$165.36</td><td>$150.77</td><td>$154.11</td><td>$3,259,712,887</td><td style="text-align: right;">$45,922,341,980</td></tr>,
     <tr><td style="text-align: left;">Oct 05, 2021</td><td>$166.99</td><td>$169.98</td><td>$160.59</td><td>$164.12</td><td>$2,541,087,419</td><td style="text-align: right;">$48,902,559,644</td></tr>,
     <tr><td style="text-align: left;">Oct 04, 2021</td><td>$172.96</td><td>$172.96</td><td>$162.77</td><td>$166.73</td><td>$3,109,040,100</td><td style="text-align: right;">$49,659,370,563</td></tr>,
     <tr><td style="text-align: left;">Oct 03, 2021</td><td>$169.11</td><td>$176.97</td><td>$166.07</td><td>$172.59</td><td>$3,149,579,954</td><td style="text-align: right;">$51,403,969,859</td></tr>,
     <tr><td style="text-align: left;">Oct 02, 2021</td><td>$161.59</td><td>$174.90</td><td>$156.32</td><td>$169.09</td><td>$3,471,658,582</td><td style="text-align: right;">$50,362,758,463</td></tr>,
     <tr><td style="text-align: left;">Oct 01, 2021</td><td>$141.38</td><td>$164.74</td><td>$138.44</td><td>$161.68</td><td>$4,387,488,320</td><td style="text-align: right;">$48,133,442,239</td></tr>,
     <tr><td style="text-align: left;">Sep 30, 2021</td><td>$135.41</td><td>$142.85</td><td>$134.31</td><td>$141.07</td><td>$2,244,376,110</td><td style="text-align: right;">$41,975,552,359</td></tr>,
     <tr><td style="text-align: left;">Sep 29, 2021</td><td>$132.34</td><td>$140.04</td><td>$131.23</td><td>$135.35</td><td>$2,428,105,040</td><td style="text-align: right;">$40,274,326,399</td></tr>,
     <tr><td style="text-align: left;">Sep 28, 2021</td><td>$136.51</td><td>$139.29</td><td>$128.24</td><td>$131.54</td><td>$2,422,542,861</td><td style="text-align: right;">$39,121,381,241</td></tr>,
     <tr><td style="text-align: left;">Sep 27, 2021</td><td>$135.93</td><td>$148.50</td><td>$133.98</td><td>$136.73</td><td>$2,867,246,888</td><td style="text-align: right;">$40,665,406,680</td></tr>,
     <tr><td style="text-align: left;">Sep 26, 2021</td><td>$136.22</td><td>$140.78</td><td>$125.12</td><td>$135.70</td><td>$2,674,182,809</td><td style="text-align: right;">$40,359,412,133</td></tr>,
     <tr><td style="text-align: left;">Sep 25, 2021</td><td>$139.30</td><td>$144.07</td><td>$134.11</td><td>$136.18</td><td>$2,037,106,949</td><td style="text-align: right;">$40,483,409,214</td></tr>,
     <tr><td style="text-align: left;">Sep 24, 2021</td><td>$149.94</td><td>$151.20</td><td>$128.80</td><td>$139.40</td><td>$3,852,350,632</td><td style="text-align: right;">$41,439,741,432</td></tr>,
     <tr><td style="text-align: left;">Sep 23, 2021</td><td>$148.06</td><td>$152.36</td><td>$143.20</td><td>$149.75</td><td>$3,389,212,044</td><td style="text-align: right;">$44,498,459,173</td></tr>,
     <tr><td style="text-align: left;">Sep 22, 2021</td><td>$124.18</td><td>$150.94</td><td>$122.35</td><td>$147.92</td><td>$4,952,222,859</td><td style="text-align: right;">$43,948,674,199</td></tr>,
     <tr><td style="text-align: left;">Sep 21, 2021</td><td>$132.76</td><td>$144.47</td><td>$116.34</td><td>$123.95</td><td>$5,243,953,819</td><td style="text-align: right;">$36,826,034,434</td></tr>,
     <tr><td style="text-align: left;">Sep 20, 2021</td><td>$152.79</td><td>$153.39</td><td>$131.26</td><td>$132.13</td><td>$5,623,667,250</td><td style="text-align: right;">$39,239,569,158</td></tr>,
     <tr><td style="text-align: left;">Sep 19, 2021</td><td>$169.23</td><td>$170.65</td><td>$151.25</td><td>$152.52</td><td>$3,350,530,308</td><td style="text-align: right;">$45,292,491,129</td></tr>,
     <tr><td style="text-align: left;">Sep 18, 2021</td><td>$147.45</td><td>$171.14</td><td>$144.39</td><td>$169.18</td><td>$5,415,012,910</td><td style="text-align: right;">$50,219,084,924</td></tr>,
     <tr><td style="text-align: left;">Sep 17, 2021</td><td>$152.35</td><td>$153.44</td><td>$135.25</td><td>$147.59</td><td>$4,675,731,485</td><td style="text-align: right;">$43,810,237,551</td></tr>,
     <tr><td style="text-align: left;">Sep 16, 2021</td><td>$158.81</td><td>$163.12</td><td>$147.65</td><td>$152.47</td><td>$3,215,168,472</td><td style="text-align: right;">$45,259,139,925</td></tr>,
     <tr><td style="text-align: left;">Sep 15, 2021</td><td>$158.42</td><td>$166.18</td><td>$154.24</td><td>$159.12</td><td>$3,908,939,772</td><td style="text-align: right;">$47,209,150,397</td></tr>,
     <tr><td style="text-align: left;">Sep 14, 2021</td><td>$169.77</td><td>$171.30</td><td>$143.55</td><td>$158.09</td><td>$5,799,758,794</td><td style="text-align: right;">$46,905,809,823</td></tr>,
     <tr><td style="text-align: left;">Sep 13, 2021</td><td>$174.42</td><td>$174.93</td><td>$150.97</td><td>$169.27</td><td>$6,437,530,449</td><td style="text-align: right;">$49,682,465,101</td></tr>,
     <tr><td style="text-align: left;">Sep 12, 2021</td><td>$179.23</td><td>$181.57</td><td>$170.58</td><td>$174.54</td><td>$3,012,633,094</td><td style="text-align: right;">$51,204,891,389</td></tr>,
     <tr><td style="text-align: left;">Sep 11, 2021</td><td>$179.37</td><td>$193.41</td><td>$175.57</td><td>$178.87</td><td>$5,367,389,010</td><td style="text-align: right;">$52,475,356,326</td></tr>,
     <tr><td style="text-align: left;">Sep 10, 2021</td><td>$187.61</td><td>$196.95</td><td>$168.69</td><td>$179.87</td><td>$7,087,524,572</td><td style="text-align: right;">$52,738,113,948</td></tr>,
     <tr><td style="text-align: left;">Sep 09, 2021</td><td>$209.47</td><td>$214.96</td><td>$181.45</td><td>$188.20</td><td>$12,676,272,744</td><td style="text-align: right;">$55,154,395,898</td></tr>,
     <tr><td style="text-align: left;">Sep 08, 2021</td><td>$173.28</td><td>$197.99</td><td>$147.99</td><td>$191.04</td><td>$13,187,213,606</td><td style="text-align: right;">$55,944,567,504</td></tr>,
     <tr><td style="text-align: left;">Sep 07, 2021</td><td>$164.18</td><td>$194.82</td><td>$133.10</td><td>$173.15</td><td>$17,068,643,416</td><td style="text-align: right;">$50,680,710,100</td></tr>,
     <tr><td style="text-align: left;">Sep 06, 2021</td><td>$142.06</td><td>$165.88</td><td>$138.04</td><td>$164.38</td><td>$5,774,090,688</td><td style="text-align: right;">$47,900,300,588</td></tr>,
     <tr><td style="text-align: left;">Sep 05, 2021</td><td>$138.99</td><td>$145.00</td><td>$135.08</td><td>$142.07</td><td>$2,996,918,105</td><td style="text-align: right;">$41,399,255,561</td></tr>,
     <tr><td style="text-align: left;">Sep 04, 2021</td><td>$146.42</td><td>$150.43</td><td>$136.45</td><td>$139.11</td><td>$3,970,422,964</td><td style="text-align: right;">$40,517,769,039</td></tr>,
     <tr><td style="text-align: left;">Sep 03, 2021</td><td>$128.39</td><td>$148.83</td><td>$128.39</td><td>$146.58</td><td>$7,526,373,837</td><td style="text-align: right;">$42,693,513,645</td></tr>,
     <tr><td style="text-align: left;">Sep 02, 2021</td><td>$110.73</td><td>$131.96</td><td>$109.65</td><td>$128.10</td><td>$5,074,399,603</td><td style="text-align: right;">$37,259,468,690</td></tr>,
     <tr><td style="text-align: left;">Sep 01, 2021</td><td>$107.44</td><td>$119.53</td><td>$106.27</td><td>$111.03</td><td>$3,974,443,896</td><td style="text-align: right;">$32,279,142,628</td></tr>,
     <tr><td style="text-align: left;">Aug 31, 2021</td><td>$109.76</td><td>$130.01</td><td>$103.35</td><td>$108.48</td><td>$7,590,894,022</td><td style="text-align: right;">$31,578,154,529</td></tr>,
     <tr><td style="text-align: left;">Aug 30, 2021</td><td>$94.34</td><td>$116.85</td><td>$94.04</td><td>$110.54</td><td>$5,274,104,165</td><td style="text-align: right;">$32,162,385,738</td></tr>,
     <tr><td style="text-align: left;">Aug 29, 2021</td><td>$96.56</td><td>$97.78</td><td>$90.99</td><td>$94.47</td><td>$1,830,344,091</td><td style="text-align: right;">$27,485,451,270</td></tr>,
     <tr><td style="text-align: left;">Aug 28, 2021</td><td>$88.00</td><td>$97.84</td><td>$85.79</td><td>$96.70</td><td>$2,580,080,503</td><td style="text-align: right;">$28,135,310,599</td></tr>,
     <tr><td style="text-align: left;">Aug 27, 2021</td><td>$74.81</td><td>$88.85</td><td>$72.72</td><td>$88.09</td><td>$3,263,988,286</td><td style="text-align: right;">$25,615,973,857</td></tr>,
     <tr><td style="text-align: left;">Aug 26, 2021</td><td>$71.97</td><td>$78.06</td><td>$66.26</td><td>$75.32</td><td>$2,713,050,538</td><td style="text-align: right;">$21,902,216,868</td></tr>,
     <tr><td style="text-align: left;">Aug 25, 2021</td><td>$70.68</td><td>$72.70</td><td>$66.22</td><td>$71.95</td><td>$1,551,240,766</td><td style="text-align: right;">$20,923,790,994</td></tr>,
     <tr><td style="text-align: left;">Aug 24, 2021</td><td>$75.78</td><td>$79.37</td><td>$68.62</td><td>$70.67</td><td>$2,153,611,667</td><td style="text-align: right;">$20,541,377,500</td></tr>,
     <tr><td style="text-align: left;">Aug 23, 2021</td><td>$72.77</td><td>$76.71</td><td>$71.68</td><td>$75.71</td><td>$1,372,134,245</td><td style="text-align: right;">$21,708,006,370</td></tr>,
     <tr><td style="text-align: left;">Aug 22, 2021</td><td>$73.87</td><td>$77.48</td><td>$71.55</td><td>$72.80</td><td>$968,933,849</td><td style="text-align: right;">$20,875,322,466</td></tr>,
     <tr><td style="text-align: left;">Aug 21, 2021</td><td>$78.70</td><td>$81.81</td><td>$72.70</td><td>$73.76</td><td>$1,513,097,171</td><td style="text-align: right;">$21,137,257,124</td></tr>,
     <tr><td style="text-align: left;">Aug 20, 2021</td><td>$72.75</td><td>$79.99</td><td>$70.94</td><td>$78.72</td><td>$1,844,455,899</td><td style="text-align: right;">$22,561,143,908</td></tr>,
     <tr><td style="text-align: left;">Aug 19, 2021</td><td>$72.84</td><td>$75.09</td><td>$68.61</td><td>$72.76</td><td>$2,467,398,203</td><td style="text-align: right;">$20,840,771,193</td></tr>,
     <tr><td style="text-align: left;">Aug 18, 2021</td><td>$64.17</td><td>$80.12</td><td>$60.27</td><td>$72.54</td><td>$4,507,409,622</td><td style="text-align: right;">$20,779,131,389</td></tr>,
     <tr><td style="text-align: left;">Aug 17, 2021</td><td>$62.12</td><td>$74.89</td><td>$58.98</td><td>$64.21</td><td>$4,043,742,154</td><td style="text-align: right;">$18,392,377,588</td></tr>,
     <tr><td style="text-align: left;">Aug 16, 2021</td><td>$53.54</td><td>$68.82</td><td>$52.47</td><td>$62.43</td><td>$3,799,339,365</td><td style="text-align: right;">$17,874,089,307</td></tr>,
     <tr><td style="text-align: left;">Aug 15, 2021</td><td>$44.15</td><td>$54.63</td><td>$43.45</td><td>$53.75</td><td>$1,448,656,564</td><td style="text-align: right;">$15,386,975,521</td></tr>,
     <tr><td style="text-align: left;">Aug 14, 2021</td><td>$44.85</td><td>$44.87</td><td>$42.94</td><td>$44.11</td><td>$363,834,257</td><td style="text-align: right;">$12,629,306,463</td></tr>,
     <tr><td style="text-align: left;">Aug 13, 2021</td><td>$41.11</td><td>$44.90</td><td>$40.72</td><td>$44.89</td><td>$541,894,525</td><td style="text-align: right;">$12,769,451,326</td></tr>,
     <tr><td style="text-align: left;">Aug 12, 2021</td><td>$41.70</td><td>$43.40</td><td>$39.38</td><td>$41.10</td><td>$527,833,804</td><td style="text-align: right;">$11,689,996,880</td></tr>,
     <tr><td style="text-align: left;">Aug 11, 2021</td><td>$40.65</td><td>$43.74</td><td>$40.63</td><td>$41.74</td><td>$507,980,107</td><td style="text-align: right;">$11,872,222,934</td></tr>,
     <tr><td style="text-align: left;">Aug 10, 2021</td><td>$38.68</td><td>$41.66</td><td>$38.22</td><td>$40.64</td><td>$452,480,699</td><td style="text-align: right;">$11,079,929,651</td></tr>,
     <tr><td style="text-align: left;">Aug 09, 2021</td><td>$37.66</td><td>$40.00</td><td>$36.48</td><td>$38.77</td><td>$377,034,585</td><td style="text-align: right;">$10,569,548,743</td></tr>,
     <tr><td style="text-align: left;">Aug 08, 2021</td><td>$39.47</td><td>$39.53</td><td>$36.94</td><td>$37.67</td><td>$358,570,315</td><td style="text-align: right;">$10,271,294,580</td></tr>,
     <tr><td style="text-align: left;">Aug 07, 2021</td><td>$39.49</td><td>$40.51</td><td>$37.63</td><td>$39.40</td><td>$534,979,916</td><td style="text-align: right;">$10,742,861,246</td></tr>,
     <tr><td style="text-align: left;">Aug 06, 2021</td><td>$37.36</td><td>$40.39</td><td>$35.69</td><td>$39.45</td><td>$589,190,671</td><td style="text-align: right;">$10,754,484,235</td></tr>,
     <tr><td style="text-align: left;">Aug 05, 2021</td><td>$35.77</td><td>$38.21</td><td>$35.53</td><td>$37.36</td><td>$595,137,193</td><td style="text-align: right;">$10,184,408,504</td></tr>,
     <tr><td style="text-align: left;">Aug 04, 2021</td><td>$34.11</td><td>$36.65</td><td>$33.27</td><td>$35.76</td><td>$413,657,602</td><td style="text-align: right;">$9,750,503,201</td></tr>,
     <tr><td style="text-align: left;">Aug 03, 2021</td><td>$33.19</td><td>$35.83</td><td>$32.40</td><td>$34.00</td><td>$474,629,269</td><td style="text-align: right;">$9,268,701,567</td></tr>,
     <tr><td style="text-align: left;">Aug 02, 2021</td><td>$34.19</td><td>$35.91</td><td>$33.06</td><td>$33.22</td><td>$407,399,691</td><td style="text-align: right;">$9,057,674,911</td></tr>,
     <tr><td style="text-align: left;">Aug 01, 2021</td><td>$36.68</td><td>$36.72</td><td>$33.28</td><td>$34.25</td><td>$490,639,931</td><td style="text-align: right;">$9,339,020,651</td></tr>,
     <tr><td style="text-align: left;">Jul 31, 2021</td><td>$32.35</td><td>$36.87</td><td>$31.68</td><td>$36.83</td><td>$587,168,181</td><td style="text-align: right;">$10,040,503,858</td></tr>,
     <tr><td style="text-align: left;">Jul 30, 2021</td><td>$31.28</td><td>$33.06</td><td>$30.07</td><td>$32.39</td><td>$617,830,199</td><td style="text-align: right;">$8,831,801,354</td></tr>,
     <tr><td style="text-align: left;">Jul 29, 2021</td><td>$27.88</td><td>$31.89</td><td>$27.37</td><td>$31.28</td><td>$448,009,571</td><td style="text-align: right;">$8,528,409,074</td></tr>,
     <tr><td style="text-align: left;">Jul 28, 2021</td><td>$28.15</td><td>$28.75</td><td>$27.41</td><td>$27.82</td><td>$315,682,626</td><td style="text-align: right;">$7,583,522,026</td></tr>,
     <tr><td style="text-align: left;">Jul 27, 2021</td><td>$28.21</td><td>$28.95</td><td>$27.01</td><td>$28.07</td><td>$375,599,550</td><td style="text-align: right;">$7,651,658,236</td></tr>,
     <tr><td style="text-align: left;">Jul 26, 2021</td><td>$28.23</td><td>$31.05</td><td>$27.90</td><td>$28.31</td><td>$743,673,802</td><td style="text-align: right;">$7,717,450,000</td></tr>,
     <tr><td style="text-align: left;">Jul 25, 2021</td><td>$28.65</td><td>$28.87</td><td>$26.53</td><td>$28.17</td><td>$309,208,018</td><td style="text-align: right;">$7,679,861,963</td></tr>,
     <tr><td style="text-align: left;">Jul 24, 2021</td><td>$28.52</td><td>$29.51</td><td>$28.07</td><td>$28.70</td><td>$353,750,758</td><td style="text-align: right;">$7,825,408,615</td></tr>,
     <tr><td style="text-align: left;">Jul 23, 2021</td><td>$27.71</td><td>$28.69</td><td>$26.43</td><td>$28.51</td><td>$407,955,237</td><td style="text-align: right;">$7,773,950,587</td></tr>,
     <tr><td style="text-align: left;">Jul 22, 2021</td><td>$26.67</td><td>$28.14</td><td>$25.95</td><td>$27.70</td><td>$364,666,998</td><td style="text-align: right;">$7,552,624,200</td></tr>,
     <tr><td style="text-align: left;">Jul 21, 2021</td><td>$23.44</td><td>$27.42</td><td>$22.87</td><td>$26.62</td><td>$555,770,206</td><td style="text-align: right;">$7,258,448,090</td></tr>,
     <tr><td style="text-align: left;">Jul 20, 2021</td><td>$24.51</td><td>$24.98</td><td>$22.18</td><td>$23.49</td><td>$413,439,963</td><td style="text-align: right;">$6,404,131,917</td></tr>,
     <tr><td style="text-align: left;">Jul 19, 2021</td><td>$26.67</td><td>$26.72</td><td>$24.01</td><td>$24.45</td><td>$361,915,410</td><td style="text-align: right;">$6,665,324,427</td></tr>,
     <tr><td style="text-align: left;">Jul 18, 2021</td><td>$26.78</td><td>$27.73</td><td>$26.36</td><td>$26.75</td><td>$230,336,396</td><td style="text-align: right;">$7,293,572,048</td></tr>,
     <tr><td style="text-align: left;">Jul 17, 2021</td><td>$26.25</td><td>$27.70</td><td>$26.04</td><td>$26.72</td><td>$289,689,475</td><td style="text-align: right;">$7,285,326,695</td></tr>,
     <tr><td style="text-align: left;">Jul 16, 2021</td><td>$28.55</td><td>$29.44</td><td>$26.23</td><td>$26.37</td><td>$374,718,328</td><td style="text-align: right;">$7,189,451,552</td></tr>,
     <tr><td style="text-align: left;">Jul 15, 2021</td><td>$31.36</td><td>$31.48</td><td>$28.01</td><td>$28.45</td><td>$329,918,376</td><td style="text-align: right;">$7,757,107,712</td></tr>,
     <tr><td style="text-align: left;">Jul 14, 2021</td><td>$29.14</td><td>$31.44</td><td>$27.52</td><td>$31.28</td><td>$331,866,434</td><td style="text-align: right;">$8,528,371,236</td></tr>,
     <tr><td style="text-align: left;">Jul 13, 2021</td><td>$30.79</td><td>$31.09</td><td>$28.92</td><td>$29.12</td><td>$197,825,362</td><td style="text-align: right;">$7,939,526,439</td></tr>,
     <tr><td style="text-align: left;">Jul 12, 2021</td><td>$32.17</td><td>$32.64</td><td>$30.07</td><td>$30.85</td><td>$221,058,993</td><td style="text-align: right;">$8,410,343,323</td></tr>,
     <tr><td style="text-align: left;">Jul 11, 2021</td><td>$31.69</td><td>$32.54</td><td>$31.41</td><td>$32.18</td><td>$211,679,810</td><td style="text-align: right;">$8,772,884,240</td></tr>,
     <tr><td style="text-align: left;">Jul 10, 2021</td><td>$33.32</td><td>$34.14</td><td>$31.19</td><td>$31.79</td><td>$296,566,657</td><td style="text-align: right;">$8,666,774,458</td></tr>,
     <tr><td style="text-align: left;">Jul 09, 2021</td><td>$33.13</td><td>$34.39</td><td>$31.99</td><td>$33.26</td><td>$327,170,629</td><td style="text-align: right;">$9,069,188,075</td></tr>,
     <tr><td style="text-align: left;">Jul 08, 2021</td><td>$36.72</td><td>$36.92</td><td>$32.80</td><td>$33.20</td><td>$498,201,257</td><td style="text-align: right;">$9,052,578,353</td></tr>,
     <tr><td style="text-align: left;">Jul 07, 2021</td><td>$34.23</td><td>$38.01</td><td>$33.84</td><td>$36.59</td><td>$519,252,659</td><td style="text-align: right;">$9,976,177,349</td></tr>,
     <tr><td style="text-align: left;">Jul 06, 2021</td><td>$32.93</td><td>$34.98</td><td>$32.93</td><td>$34.27</td><td>$365,336,040</td><td style="text-align: right;">$9,343,050,097</td></tr>,
     <tr><td style="text-align: left;">Jul 05, 2021</td><td>$34.28</td><td>$34.46</td><td>$32.48</td><td>$32.98</td><td>$313,839,322</td><td style="text-align: right;">$8,992,833,088</td></tr>,
     <tr><td style="text-align: left;">Jul 04, 2021</td><td>$34.50</td><td>$35.50</td><td>$33.56</td><td>$34.31</td><td>$303,420,520</td><td style="text-align: right;">$9,354,354,087</td></tr>,
     <tr><td style="text-align: left;">Jul 03, 2021</td><td>$34.02</td><td>$35.40</td><td>$33.30</td><td>$34.48</td><td>$327,019,964</td><td style="text-align: right;">$9,400,215,615</td></tr>,
     <tr><td style="text-align: left;">Jul 02, 2021</td><td>$33.31</td><td>$34.03</td><td>$31.48</td><td>$34.02</td><td>$440,298,780</td><td style="text-align: right;">$9,275,256,700</td></tr>,
     <tr><td style="text-align: left;">Jul 01, 2021</td><td>$35.51</td><td>$35.54</td><td>$32.39</td><td>$33.40</td><td>$474,665,321</td><td style="text-align: right;">$9,107,189,782</td></tr>,
     <tr><td style="text-align: left;">Jun 30, 2021</td><td>$33.96</td><td>$35.95</td><td>$31.60</td><td>$35.56</td><td>$570,984,168</td><td style="text-align: right;">$9,694,007,086</td></tr>,
     <tr><td style="text-align: left;">Jun 29, 2021</td><td>$33.01</td><td>$35.79</td><td>$32.73</td><td>$33.87</td><td>$471,854,279</td><td style="text-align: right;">$9,233,357,638</td></tr>,
     <tr><td style="text-align: left;">Jun 28, 2021</td><td>$31.88</td><td>$34.24</td><td>$31.04</td><td>$32.93</td><td>$473,612,135</td><td style="text-align: right;">$8,977,345,683</td></tr>,
     <tr><td style="text-align: left;">Jun 27, 2021</td><td>$29.75</td><td>$31.93</td><td>$29.27</td><td>$31.93</td><td>$497,353,288</td><td style="text-align: right;">$8,705,146,914</td></tr>,
     <tr><td style="text-align: left;">Jun 26, 2021</td><td>$28.61</td><td>$30.01</td><td>$26.71</td><td>$29.71</td><td>$560,342,710</td><td style="text-align: right;">$8,100,836,463</td></tr>,
     <tr><td style="text-align: left;">Jun 25, 2021</td><td>$31.17</td><td>$32.90</td><td>$28.04</td><td>$28.70</td><td>$632,052,177</td><td style="text-align: right;">$7,824,384,002</td></tr>,
     <tr><td style="text-align: left;">Jun 24, 2021</td><td>$30.85</td><td>$32.99</td><td>$28.55</td><td>$31.18</td><td>$641,150,364</td><td style="text-align: right;">$8,501,117,110</td></tr>,
     <tr><td style="text-align: left;">Jun 23, 2021</td><td>$26.91</td><td>$32.77</td><td>$25.70</td><td>$30.05</td><td>$1,111,302,687</td><td style="text-align: right;">$8,192,451,330</td></tr>,
     <tr><td style="text-align: left;">Jun 22, 2021</td><td>$26.59</td><td>$28.71</td><td>$20.38</td><td>$26.77</td><td>$1,258,580,061</td><td style="text-align: right;">$7,299,009,873</td></tr>,
     <tr><td style="text-align: left;">Jun 21, 2021</td><td>$35.26</td><td>$35.50</td><td>$25.95</td><td>$26.66</td><td>$760,344,541</td><td style="text-align: right;">$7,267,805,028</td></tr>,
     <tr><td style="text-align: left;">Jun 20, 2021</td><td>$35.24</td><td>$35.93</td><td>$31.36</td><td>$35.32</td><td>$452,587,531</td><td style="text-align: right;">$9,630,102,394</td></tr>,
     <tr><td style="text-align: left;">Jun 19, 2021</td><td>$36.82</td><td>$37.35</td><td>$34.98</td><td>$35.35</td><td>$264,640,750</td><td style="text-align: right;">$9,638,669,476</td></tr>]




```python
all_rows = []
for r in rows:
    row = []
    for c in r:
        row.append(c.text)
    all_rows.append(row)    
```

### 3- Convert the rows into a pandas dataframe.


```python
df = pd.DataFrame (all_rows, columns = ['Date', 'Open*', 'High', 'Low', 'Close**', 'Volume', 'Market Cap'])
```


```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Date</th>
      <th>Open*</th>
      <th>High</th>
      <th>Low</th>
      <th>Close**</th>
      <th>Volume</th>
      <th>Market Cap</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Date</td>
      <td>Open*</td>
      <td>High</td>
      <td>Low</td>
      <td>Close**</td>
      <td>Volume</td>
      <td>Market Cap</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Oct 18, 2021</td>
      <td>$160.00</td>
      <td>$162.86</td>
      <td>$155.03</td>
      <td>$157.23</td>
      <td>$1,698,878,759</td>
      <td>$47,254,003,672</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Oct 17, 2021</td>
      <td>$157.46</td>
      <td>$167.43</td>
      <td>$154.09</td>
      <td>$159.74</td>
      <td>$2,168,838,138</td>
      <td>$47,991,515,200</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Oct 16, 2021</td>
      <td>$163.01</td>
      <td>$164.71</td>
      <td>$156.74</td>
      <td>$157.54</td>
      <td>$1,531,502,795</td>
      <td>$47,304,541,727</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Oct 15, 2021</td>
      <td>$150.05</td>
      <td>$165.12</td>
      <td>$146.98</td>
      <td>$162.60</td>
      <td>$3,970,589,003</td>
      <td>$48,823,235,028</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>118</th>
      <td>Jun 23, 2021</td>
      <td>$26.91</td>
      <td>$32.77</td>
      <td>$25.70</td>
      <td>$30.05</td>
      <td>$1,111,302,687</td>
      <td>$8,192,451,330</td>
    </tr>
    <tr>
      <th>119</th>
      <td>Jun 22, 2021</td>
      <td>$26.59</td>
      <td>$28.71</td>
      <td>$20.38</td>
      <td>$26.77</td>
      <td>$1,258,580,061</td>
      <td>$7,299,009,873</td>
    </tr>
    <tr>
      <th>120</th>
      <td>Jun 21, 2021</td>
      <td>$35.26</td>
      <td>$35.50</td>
      <td>$25.95</td>
      <td>$26.66</td>
      <td>$760,344,541</td>
      <td>$7,267,805,028</td>
    </tr>
    <tr>
      <th>121</th>
      <td>Jun 20, 2021</td>
      <td>$35.24</td>
      <td>$35.93</td>
      <td>$31.36</td>
      <td>$35.32</td>
      <td>$452,587,531</td>
      <td>$9,630,102,394</td>
    </tr>
    <tr>
      <th>122</th>
      <td>Jun 19, 2021</td>
      <td>$36.82</td>
      <td>$37.35</td>
      <td>$34.98</td>
      <td>$35.35</td>
      <td>$264,640,750</td>
      <td>$9,638,669,476</td>
    </tr>
  </tbody>
</table>
<p>123 rows × 7 columns</p>
</div>



## Second: Data Cleaning, EDA and Data engineering.

### 1- remove the symbols


```python
df["Market Cap"].replace('$','', inplace= True)
```


```python
df['MarkerCap']=df['Market Cap'].apply(lambda x: x[1:].replace(',', ''))
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Date</th>
      <th>Open*</th>
      <th>High</th>
      <th>Low</th>
      <th>Close**</th>
      <th>Volume</th>
      <th>Market Cap</th>
      <th>MarkerCap</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Date</td>
      <td>Open*</td>
      <td>High</td>
      <td>Low</td>
      <td>Close**</td>
      <td>Volume</td>
      <td>Market Cap</td>
      <td>arket Cap</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Oct 18, 2021</td>
      <td>$160.00</td>
      <td>$162.86</td>
      <td>$155.03</td>
      <td>$157.23</td>
      <td>$1,698,878,759</td>
      <td>$47,254,003,672</td>
      <td>47254003672</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Oct 17, 2021</td>
      <td>$157.46</td>
      <td>$167.43</td>
      <td>$154.09</td>
      <td>$159.74</td>
      <td>$2,168,838,138</td>
      <td>$47,991,515,200</td>
      <td>47991515200</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Oct 16, 2021</td>
      <td>$163.01</td>
      <td>$164.71</td>
      <td>$156.74</td>
      <td>$157.54</td>
      <td>$1,531,502,795</td>
      <td>$47,304,541,727</td>
      <td>47304541727</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Oct 15, 2021</td>
      <td>$150.05</td>
      <td>$165.12</td>
      <td>$146.98</td>
      <td>$162.60</td>
      <td>$3,970,589,003</td>
      <td>$48,823,235,028</td>
      <td>48823235028</td>
    </tr>
  </tbody>
</table>
</div>




```python
df["Volume"].replace('$','', inplace= True)
df['VOLUME']=df['Volume'].apply(lambda x: x[1:].replace(',', ''))

```


```python
df.drop(['Market Cap','Volume'],
  axis='columns', inplace=True)
```


```python
df["Close**"].replace('$','', inplace= True)
df['CLOSE']=df['Close**'].apply(lambda x: x[1:].replace(',', ''))
```


```python
df["Low"].replace('$','', inplace= True)
df['LOW']=df['Low'].apply(lambda x: x[1:].replace(',', ''))
df["High"].replace('$','', inplace= True)
df['HIGH']=df['High'].apply(lambda x: x[1:].replace(',', ''))
df["Open*"].replace('$','', inplace= True)
df['OPEN']=df['Open*'].apply(lambda x: x[1:].replace(',', ''))
```


```python
df.drop(['High','Low','Close**','Open*'],
  axis='columns', inplace=True)
```

### 2- remove duplicates


```python
df.drop([0],inplace=True)
```


```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Date</th>
      <th>MarkerCap</th>
      <th>VOLUME</th>
      <th>CLOSE</th>
      <th>LOW</th>
      <th>HIGH</th>
      <th>OPEN</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>Oct 18, 2021</td>
      <td>47254003672</td>
      <td>1698878759</td>
      <td>157.23</td>
      <td>155.03</td>
      <td>162.86</td>
      <td>160.00</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Oct 17, 2021</td>
      <td>47991515200</td>
      <td>2168838138</td>
      <td>159.74</td>
      <td>154.09</td>
      <td>167.43</td>
      <td>157.46</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Oct 16, 2021</td>
      <td>47304541727</td>
      <td>1531502795</td>
      <td>157.54</td>
      <td>156.74</td>
      <td>164.71</td>
      <td>163.01</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Oct 15, 2021</td>
      <td>48823235028</td>
      <td>3970589003</td>
      <td>162.60</td>
      <td>146.98</td>
      <td>165.12</td>
      <td>150.05</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Oct 14, 2021</td>
      <td>44950465986</td>
      <td>1948101208</td>
      <td>149.76</td>
      <td>147.33</td>
      <td>155.33</td>
      <td>148.02</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>118</th>
      <td>Jun 23, 2021</td>
      <td>8192451330</td>
      <td>1111302687</td>
      <td>30.05</td>
      <td>25.70</td>
      <td>32.77</td>
      <td>26.91</td>
    </tr>
    <tr>
      <th>119</th>
      <td>Jun 22, 2021</td>
      <td>7299009873</td>
      <td>1258580061</td>
      <td>26.77</td>
      <td>20.38</td>
      <td>28.71</td>
      <td>26.59</td>
    </tr>
    <tr>
      <th>120</th>
      <td>Jun 21, 2021</td>
      <td>7267805028</td>
      <td>760344541</td>
      <td>26.66</td>
      <td>25.95</td>
      <td>35.50</td>
      <td>35.26</td>
    </tr>
    <tr>
      <th>121</th>
      <td>Jun 20, 2021</td>
      <td>9630102394</td>
      <td>452587531</td>
      <td>35.32</td>
      <td>31.36</td>
      <td>35.93</td>
      <td>35.24</td>
    </tr>
    <tr>
      <th>122</th>
      <td>Jun 19, 2021</td>
      <td>9638669476</td>
      <td>264640750</td>
      <td>35.35</td>
      <td>34.98</td>
      <td>37.35</td>
      <td>36.82</td>
    </tr>
  </tbody>
</table>
<p>122 rows × 7 columns</p>
</div>



### 3- Convert the type of Date column into a datetime type.


```python
nDate=[]
for s in df.Date:
    d = datetime.strptime(s, '%b %d, %Y')
    nDate.append(d.strftime('%Y-%m-%d'))
    print(d.strftime('%Y-%m-%d'))
```

    2021-10-18
    2021-10-17
    2021-10-16
    2021-10-15
    2021-10-14
    2021-10-13
    2021-10-12
    2021-10-11
    2021-10-10
    2021-10-09
    2021-10-08
    2021-10-07
    2021-10-06
    2021-10-05
    2021-10-04
    2021-10-03
    2021-10-02
    2021-10-01
    2021-09-30
    2021-09-29
    2021-09-28
    2021-09-27
    2021-09-26
    2021-09-25
    2021-09-24
    2021-09-23
    2021-09-22
    2021-09-21
    2021-09-20
    2021-09-19
    2021-09-18
    2021-09-17
    2021-09-16
    2021-09-15
    2021-09-14
    2021-09-13
    2021-09-12
    2021-09-11
    2021-09-10
    2021-09-09
    2021-09-08
    2021-09-07
    2021-09-06
    2021-09-05
    2021-09-04
    2021-09-03
    2021-09-02
    2021-09-01
    2021-08-31
    2021-08-30
    2021-08-29
    2021-08-28
    2021-08-27
    2021-08-26
    2021-08-25
    2021-08-24
    2021-08-23
    2021-08-22
    2021-08-21
    2021-08-20
    2021-08-19
    2021-08-18
    2021-08-17
    2021-08-16
    2021-08-15
    2021-08-14
    2021-08-13
    2021-08-12
    2021-08-11
    2021-08-10
    2021-08-09
    2021-08-08
    2021-08-07
    2021-08-06
    2021-08-05
    2021-08-04
    2021-08-03
    2021-08-02
    2021-08-01
    2021-07-31
    2021-07-30
    2021-07-29
    2021-07-28
    2021-07-27
    2021-07-26
    2021-07-25
    2021-07-24
    2021-07-23
    2021-07-22
    2021-07-21
    2021-07-20
    2021-07-19
    2021-07-18
    2021-07-17
    2021-07-16
    2021-07-15
    2021-07-14
    2021-07-13
    2021-07-12
    2021-07-11
    2021-07-10
    2021-07-09
    2021-07-08
    2021-07-07
    2021-07-06
    2021-07-05
    2021-07-04
    2021-07-03
    2021-07-02
    2021-07-01
    2021-06-30
    2021-06-29
    2021-06-28
    2021-06-27
    2021-06-26
    2021-06-25
    2021-06-24
    2021-06-23
    2021-06-22
    2021-06-21
    2021-06-20
    2021-06-19
    


```python
df['DATE']= nDate
```


```python
df.drop(['Date'], axis=1,inplace=True)
```


```python
df['DATE'] = pd.to_datetime(df['DATE'], format='%Y-%m-%d')

```

### 4- Convert the types of all other columns into a float.


```python
df.dtypes
```




    MarkerCap    object
    VOLUME       object
    CLOSE        object
    LOW          object
    HIGH         object
    OPEN         object
    DATE         object
    dtype: object




```python
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>MarkerCap</th>
      <th>VOLUME</th>
      <th>CLOSE</th>
      <th>LOW</th>
      <th>HIGH</th>
      <th>OPEN</th>
      <th>DATE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>47254003672</td>
      <td>1698878759</td>
      <td>157.23</td>
      <td>155.03</td>
      <td>162.86</td>
      <td>160.00</td>
      <td>2021-10-18</td>
    </tr>
    <tr>
      <th>2</th>
      <td>47991515200</td>
      <td>2168838138</td>
      <td>159.74</td>
      <td>154.09</td>
      <td>167.43</td>
      <td>157.46</td>
      <td>2021-10-17</td>
    </tr>
    <tr>
      <th>3</th>
      <td>47304541727</td>
      <td>1531502795</td>
      <td>157.54</td>
      <td>156.74</td>
      <td>164.71</td>
      <td>163.01</td>
      <td>2021-10-16</td>
    </tr>
    <tr>
      <th>4</th>
      <td>48823235028</td>
      <td>3970589003</td>
      <td>162.60</td>
      <td>146.98</td>
      <td>165.12</td>
      <td>150.05</td>
      <td>2021-10-15</td>
    </tr>
    <tr>
      <th>5</th>
      <td>44950465986</td>
      <td>1948101208</td>
      <td>149.76</td>
      <td>147.33</td>
      <td>155.33</td>
      <td>148.02</td>
      <td>2021-10-14</td>
    </tr>
  </tbody>
</table>
</div>




```python
df = df.astype({"CLOSE": float,"LOW": float ,"HIGH": float ,"OPEN": float, "MarkerCap": float , "VOLUME": float})
```


```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    Int64Index: 122 entries, 1 to 122
    Data columns (total 7 columns):
     #   Column     Non-Null Count  Dtype         
    ---  ------     --------------  -----         
     0   MarkerCap  122 non-null    float64       
     1   VOLUME     122 non-null    float64       
     2   CLOSE      122 non-null    float64       
     3   LOW        122 non-null    float64       
     4   HIGH       122 non-null    float64       
     5   OPEN       122 non-null    float64       
     6   DATE       122 non-null    datetime64[ns]
    dtypes: datetime64[ns](1), float64(6)
    memory usage: 7.6 KB
    

### 5- np.log for ( 'MarkerCap' ) and  ( 'VOLUME' ) columns.


```python
df['nMarketCap'] = np.log(df['MarkerCap'])
df['nVOLUME'] = np.log(df['VOLUME'])
df.drop(['MarkerCap'], axis=1,inplace=True)
df.drop(['VOLUME'], axis=1,inplace=True)
```


```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>CLOSE</th>
      <th>LOW</th>
      <th>HIGH</th>
      <th>OPEN</th>
      <th>DATE</th>
      <th>nMarketCap</th>
      <th>nVOLUME</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>157.23</td>
      <td>155.03</td>
      <td>162.86</td>
      <td>160.00</td>
      <td>2021-10-18</td>
      <td>24.578803</td>
      <td>21.253234</td>
    </tr>
    <tr>
      <th>2</th>
      <td>159.74</td>
      <td>154.09</td>
      <td>167.43</td>
      <td>157.46</td>
      <td>2021-10-17</td>
      <td>24.594290</td>
      <td>21.497457</td>
    </tr>
    <tr>
      <th>3</th>
      <td>157.54</td>
      <td>156.74</td>
      <td>164.71</td>
      <td>163.01</td>
      <td>2021-10-16</td>
      <td>24.579872</td>
      <td>21.149515</td>
    </tr>
    <tr>
      <th>4</th>
      <td>162.60</td>
      <td>146.98</td>
      <td>165.12</td>
      <td>150.05</td>
      <td>2021-10-15</td>
      <td>24.611472</td>
      <td>22.102180</td>
    </tr>
    <tr>
      <th>5</th>
      <td>149.76</td>
      <td>147.33</td>
      <td>155.33</td>
      <td>148.02</td>
      <td>2021-10-14</td>
      <td>24.528827</td>
      <td>21.390121</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>118</th>
      <td>30.05</td>
      <td>25.70</td>
      <td>32.77</td>
      <td>26.91</td>
      <td>2021-06-23</td>
      <td>22.826479</td>
      <td>20.828799</td>
    </tr>
    <tr>
      <th>119</th>
      <td>26.77</td>
      <td>20.38</td>
      <td>28.71</td>
      <td>26.59</td>
      <td>2021-06-22</td>
      <td>22.711005</td>
      <td>20.953250</td>
    </tr>
    <tr>
      <th>120</th>
      <td>26.66</td>
      <td>25.95</td>
      <td>35.50</td>
      <td>35.26</td>
      <td>2021-06-21</td>
      <td>22.706720</td>
      <td>20.449282</td>
    </tr>
    <tr>
      <th>121</th>
      <td>35.32</td>
      <td>31.36</td>
      <td>35.93</td>
      <td>35.24</td>
      <td>2021-06-20</td>
      <td>22.988160</td>
      <td>19.930492</td>
    </tr>
    <tr>
      <th>122</th>
      <td>35.35</td>
      <td>34.98</td>
      <td>37.35</td>
      <td>36.82</td>
      <td>2021-06-19</td>
      <td>22.989049</td>
      <td>19.393884</td>
    </tr>
  </tbody>
</table>
<p>122 rows × 7 columns</p>
</div>




```python
df.drop(['MarkerCap'], axis=1,inplace=True)
df.drop(['VOLUME'], axis=1,inplace=True)
```

### 6- Rearrange the datafame date by weeks.


```python
weekly_df= df.resample('W', on ='DATE').mean()

```


```python
weekly_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>CLOSE</th>
      <th>LOW</th>
      <th>HIGH</th>
      <th>OPEN</th>
      <th>nMarketCap</th>
      <th>nVOLUME</th>
    </tr>
    <tr>
      <th>DATE</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2021-06-20</th>
      <td>35.335000</td>
      <td>33.170000</td>
      <td>36.640000</td>
      <td>36.030000</td>
      <td>22.988604</td>
      <td>19.662188</td>
    </tr>
    <tr>
      <th>2021-06-27</th>
      <td>29.285714</td>
      <td>26.371429</td>
      <td>32.115714</td>
      <td>29.877143</td>
      <td>22.798656</td>
      <td>20.420494</td>
    </tr>
    <tr>
      <th>2021-07-04</th>
      <td>34.081429</td>
      <td>32.300000</td>
      <td>35.207143</td>
      <td>33.741429</td>
      <td>22.952126</td>
      <td>19.875457</td>
    </tr>
    <tr>
      <th>2021-07-11</th>
      <td>33.467143</td>
      <td>32.377143</td>
      <td>35.062857</td>
      <td>33.757143</td>
      <td>22.933317</td>
      <td>19.665642</td>
    </tr>
    <tr>
      <th>2021-07-18</th>
      <td>28.505714</td>
      <td>27.592857</td>
      <td>30.217143</td>
      <td>29.291429</td>
      <td>22.771665</td>
      <td>19.433213</td>
    </tr>
    <tr>
      <th>2021-07-25</th>
      <td>26.805714</td>
      <td>25.148571</td>
      <td>27.761429</td>
      <td>26.595714</td>
      <td>22.709649</td>
      <td>19.779657</td>
    </tr>
    <tr>
      <th>2021-08-01</th>
      <td>31.278571</td>
      <td>29.245714</td>
      <td>32.470000</td>
      <td>30.397143</td>
      <td>22.861405</td>
      <td>20.015070</td>
    </tr>
    <tr>
      <th>2021-08-08</th>
      <td>36.694286</td>
      <td>34.931429</td>
      <td>38.147143</td>
      <td>36.225714</td>
      <td>23.024316</td>
      <td>19.976834</td>
    </tr>
    <tr>
      <th>2021-08-15</th>
      <td>43.571429</td>
      <td>40.260000</td>
      <td>44.742857</td>
      <td>41.257143</td>
      <td>23.225072</td>
      <td>20.103577</td>
    </tr>
    <tr>
      <th>2021-08-22</th>
      <td>71.031429</td>
      <td>65.074286</td>
      <td>76.885714</td>
      <td>68.284286</td>
      <td>23.733549</td>
      <td>21.599790</td>
    </tr>
    <tr>
      <th>2021-08-29</th>
      <td>81.844286</td>
      <td>74.611429</td>
      <td>84.472857</td>
      <td>78.652857</td>
      <td>23.883479</td>
      <td>21.474111</td>
    </tr>
    <tr>
      <th>2021-09-05</th>
      <td>126.558571</td>
      <td>116.175714</td>
      <td>134.658571</td>
      <td>119.438571</td>
      <td>24.322500</td>
      <td>22.321655</td>
    </tr>
    <tr>
      <th>2021-09-12</th>
      <td>178.578571</td>
      <td>159.345714</td>
      <td>192.225714</td>
      <td>176.457143</td>
      <td>24.679078</td>
      <td>22.787708</td>
    </tr>
    <tr>
      <th>2021-09-19</th>
      <td>158.320000</td>
      <td>146.757143</td>
      <td>167.251429</td>
      <td>161.492857</td>
      <td>24.570436</td>
      <td>22.236378</td>
    </tr>
    <tr>
      <th>2021-09-26</th>
      <td>137.861429</td>
      <td>128.740000</td>
      <td>148.172857</td>
      <td>140.464286</td>
      <td>24.434312</td>
      <td>22.044459</td>
    </tr>
    <tr>
      <th>2021-10-03</th>
      <td>149.721429</td>
      <td>141.227143</td>
      <td>155.327143</td>
      <td>144.610000</td>
      <td>24.514379</td>
      <td>21.795318</td>
    </tr>
    <tr>
      <th>2021-10-10</th>
      <td>157.581429</td>
      <td>154.171429</td>
      <td>165.468571</td>
      <td>161.175714</td>
      <td>24.573918</td>
      <td>21.592111</td>
    </tr>
    <tr>
      <th>2021-10-17</th>
      <td>153.631429</td>
      <td>146.817143</td>
      <td>159.302857</td>
      <td>151.981429</td>
      <td>24.553381</td>
      <td>21.531196</td>
    </tr>
    <tr>
      <th>2021-10-24</th>
      <td>157.230000</td>
      <td>155.030000</td>
      <td>162.860000</td>
      <td>160.000000</td>
      <td>24.578803</td>
      <td>21.253234</td>
    </tr>
  </tbody>
</table>
</div>




```python
plt.figure(figsize=(10,10))
weekly_df.plot();

```


    <Figure size 720x720 with 0 Axes>



    
![png](output_45_1.png)
    



```python
df.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>MarkerCap</th>
      <th>VOLUME</th>
      <th>CLOSE</th>
      <th>LOW</th>
      <th>HIGH</th>
      <th>OPEN</th>
      <th>DATE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>122</td>
      <td>122</td>
      <td>122</td>
      <td>122</td>
      <td>122</td>
      <td>122</td>
      <td>122</td>
    </tr>
    <tr>
      <th>unique</th>
      <td>122</td>
      <td>122</td>
      <td>120</td>
      <td>120</td>
      <td>121</td>
      <td>121</td>
      <td>122</td>
    </tr>
    <tr>
      <th>top</th>
      <td>8100836463</td>
      <td>471854279</td>
      <td>31.28</td>
      <td>30.07</td>
      <td>35.50</td>
      <td>26.67</td>
      <td>2021-09-05</td>
    </tr>
    <tr>
      <th>freq</th>
      <td>1</td>
      <td>1</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python

```

# Third: ARIMA(p,d,q).

### 1- Autocorrelation function (ACF).


```python
x= weekly_df.filter(['nMarketCap'],axis=1)
x.drop(x.tail(1).index,inplace=True
plot_acf(x)
```




    
![png](output_50_0.png)
    




    
![png](output_50_1.png)
    


### 2- split the data.



```python
x= weekly_df.filter(['nMarketCap'],axis=1)
train = x[0:12]
test= x[12:]
```


```python
x
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>nMarketCap</th>
    </tr>
    <tr>
      <th>DATE</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2021-06-20</th>
      <td>22.988604</td>
    </tr>
    <tr>
      <th>2021-06-27</th>
      <td>22.798656</td>
    </tr>
    <tr>
      <th>2021-07-04</th>
      <td>22.952126</td>
    </tr>
    <tr>
      <th>2021-07-11</th>
      <td>22.933317</td>
    </tr>
    <tr>
      <th>2021-07-18</th>
      <td>22.771665</td>
    </tr>
    <tr>
      <th>2021-07-25</th>
      <td>22.709649</td>
    </tr>
    <tr>
      <th>2021-08-01</th>
      <td>22.861405</td>
    </tr>
    <tr>
      <th>2021-08-08</th>
      <td>23.024316</td>
    </tr>
    <tr>
      <th>2021-08-15</th>
      <td>23.225072</td>
    </tr>
    <tr>
      <th>2021-08-22</th>
      <td>23.733549</td>
    </tr>
    <tr>
      <th>2021-08-29</th>
      <td>23.883479</td>
    </tr>
    <tr>
      <th>2021-09-05</th>
      <td>24.322500</td>
    </tr>
    <tr>
      <th>2021-09-12</th>
      <td>24.679078</td>
    </tr>
    <tr>
      <th>2021-09-19</th>
      <td>24.570436</td>
    </tr>
    <tr>
      <th>2021-09-26</th>
      <td>24.434312</td>
    </tr>
    <tr>
      <th>2021-10-03</th>
      <td>24.514379</td>
    </tr>
    <tr>
      <th>2021-10-10</th>
      <td>24.573918</td>
    </tr>
    <tr>
      <th>2021-10-17</th>
      <td>24.553381</td>
    </tr>
  </tbody>
</table>
</div>



### 3- Collect parameters and train/fit them.


```python
p=q= range(0,7)
d=range(1,3)
pdq= list(itertools.product(p,d,q))
pdq
```




    [(0, 1, 0),
     (0, 1, 1),
     (0, 1, 2),
     (0, 1, 3),
     (0, 1, 4),
     (0, 1, 5),
     (0, 1, 6),
     (0, 2, 0),
     (0, 2, 1),
     (0, 2, 2),
     (0, 2, 3),
     (0, 2, 4),
     (0, 2, 5),
     (0, 2, 6),
     (1, 1, 0),
     (1, 1, 1),
     (1, 1, 2),
     (1, 1, 3),
     (1, 1, 4),
     (1, 1, 5),
     (1, 1, 6),
     (1, 2, 0),
     (1, 2, 1),
     (1, 2, 2),
     (1, 2, 3),
     (1, 2, 4),
     (1, 2, 5),
     (1, 2, 6),
     (2, 1, 0),
     (2, 1, 1),
     (2, 1, 2),
     (2, 1, 3),
     (2, 1, 4),
     (2, 1, 5),
     (2, 1, 6),
     (2, 2, 0),
     (2, 2, 1),
     (2, 2, 2),
     (2, 2, 3),
     (2, 2, 4),
     (2, 2, 5),
     (2, 2, 6),
     (3, 1, 0),
     (3, 1, 1),
     (3, 1, 2),
     (3, 1, 3),
     (3, 1, 4),
     (3, 1, 5),
     (3, 1, 6),
     (3, 2, 0),
     (3, 2, 1),
     (3, 2, 2),
     (3, 2, 3),
     (3, 2, 4),
     (3, 2, 5),
     (3, 2, 6),
     (4, 1, 0),
     (4, 1, 1),
     (4, 1, 2),
     (4, 1, 3),
     (4, 1, 4),
     (4, 1, 5),
     (4, 1, 6),
     (4, 2, 0),
     (4, 2, 1),
     (4, 2, 2),
     (4, 2, 3),
     (4, 2, 4),
     (4, 2, 5),
     (4, 2, 6),
     (5, 1, 0),
     (5, 1, 1),
     (5, 1, 2),
     (5, 1, 3),
     (5, 1, 4),
     (5, 1, 5),
     (5, 1, 6),
     (5, 2, 0),
     (5, 2, 1),
     (5, 2, 2),
     (5, 2, 3),
     (5, 2, 4),
     (5, 2, 5),
     (5, 2, 6),
     (6, 1, 0),
     (6, 1, 1),
     (6, 1, 2),
     (6, 1, 3),
     (6, 1, 4),
     (6, 1, 5),
     (6, 1, 6),
     (6, 2, 0),
     (6, 2, 1),
     (6, 2, 2),
     (6, 2, 3),
     (6, 2, 4),
     (6, 2, 5),
     (6, 2, 6)]




```python
warnings.filterwarnings('ignore')
for param in pdq:
    try:
        arima_model= ARIMA(train, order=param)
        arima_model_fit = arima_model.fit()
        predictions = arima_model_fit.forecast(steps= 6)[0]
        predictions= pd.Series(predictions)
        print( param,f'AIC score  {arima_model_fit.aic}', f'MAE score  {np.mean(np.abs(test.values-predictions.values))}')
    except:
        continue
```

    (0, 1, 0) AIC score  1.034454568498095 MAE score  0.23715581916827747
    (0, 1, 1) AIC score  2.452191599839715 MAE score  0.2829520538793745
    (0, 1, 2) AIC score  1.6377112000037002 MAE score  0.42002567978206407
    (0, 1, 3) AIC score  2.5608149414368384 MAE score  0.38864783253830854
    (0, 1, 4) AIC score  4.9436277197310545 MAE score  0.7145732029701998
    (0, 2, 0) AIC score  2.2695834901955134 MAE score  1.8918604413017155
    (0, 2, 1) AIC score  -2.3243832413030674 MAE score  1.552793030117795
    (0, 2, 2) AIC score  -0.7086227840312915 MAE score  1.52834080853946
    (0, 2, 3) AIC score  0.41776440266239945 MAE score  1.5754591563663287
    (1, 1, 0) AIC score  1.910492155425942 MAE score  0.3715153909186903
    (1, 2, 0) AIC score  0.8958101700660492 MAE score  1.3426637044680199
    (2, 1, 0) AIC score  2.355847158987622 MAE score  0.5030365408266051
    (2, 2, 0) AIC score  1.1143952517700768 MAE score  1.6139028882551
    (3, 1, 0) AIC score  4.301779727228656 MAE score  0.5691860087016045
    (3, 2, 0) AIC score  2.8183783436173755 MAE score  1.6366175214496628
    (4, 1, 0) AIC score  5.634756748299985 MAE score  0.4326931992372851
    (4, 2, 0) AIC score  37.97138515318035 MAE score  1.959951945272203
    (5, 1, 0) AIC score  48.831155392198866 MAE score  0.8775976511028473
    

### 4- Determine the best parameter for your model depending on AIC and MAE scores.

### After fitting multiple parameters we found out that the best ARIMA model for our data is ARIMA(0,1,0) 
### with AIC score = 1.034454568498095 and MAE score = 0.23715581916827747


```python
arima_model= ARIMA(train, order= (0,1,0))
arima_model_fit = arima_model.fit()
```


```python
predictions = arima_model_fit.forecast(steps= 6)[0]
predictions= pd.Series(predictions)

```


```python
test_pre1= test.copy()
test_pre1['predictions']= predictions.values
test_pre1
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>nMarketCap</th>
      <th>predictions</th>
    </tr>
    <tr>
      <th>DATE</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2021-09-12</th>
      <td>24.679078</td>
      <td>24.443764</td>
    </tr>
    <tr>
      <th>2021-09-19</th>
      <td>24.570436</td>
      <td>24.565027</td>
    </tr>
    <tr>
      <th>2021-09-26</th>
      <td>24.434312</td>
      <td>24.686290</td>
    </tr>
    <tr>
      <th>2021-10-03</th>
      <td>24.514379</td>
      <td>24.807553</td>
    </tr>
    <tr>
      <th>2021-10-10</th>
      <td>24.573918</td>
      <td>24.928817</td>
    </tr>
    <tr>
      <th>2021-10-17</th>
      <td>24.553381</td>
      <td>25.050080</td>
    </tr>
  </tbody>
</table>
</div>




```python
frames = [train.copy(),test_pre1.copy()]

result = pd.concat(frames)
result
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>nMarketCap</th>
      <th>predictions</th>
    </tr>
    <tr>
      <th>DATE</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2021-06-20</th>
      <td>22.988604</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2021-06-27</th>
      <td>22.798656</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2021-07-04</th>
      <td>22.952126</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2021-07-11</th>
      <td>22.933317</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2021-07-18</th>
      <td>22.771665</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2021-07-25</th>
      <td>22.709649</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2021-08-01</th>
      <td>22.861405</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2021-08-08</th>
      <td>23.024316</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2021-08-15</th>
      <td>23.225072</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2021-08-22</th>
      <td>23.733549</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2021-08-29</th>
      <td>23.883479</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2021-09-05</th>
      <td>24.322500</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2021-09-12</th>
      <td>24.679078</td>
      <td>24.443764</td>
    </tr>
    <tr>
      <th>2021-09-19</th>
      <td>24.570436</td>
      <td>24.565027</td>
    </tr>
    <tr>
      <th>2021-09-26</th>
      <td>24.434312</td>
      <td>24.686290</td>
    </tr>
    <tr>
      <th>2021-10-03</th>
      <td>24.514379</td>
      <td>24.807553</td>
    </tr>
    <tr>
      <th>2021-10-10</th>
      <td>24.573918</td>
      <td>24.928817</td>
    </tr>
    <tr>
      <th>2021-10-17</th>
      <td>24.553381</td>
      <td>25.050080</td>
    </tr>
  </tbody>
</table>
</div>




```python
fig, ax = plt.subplots(figsize=(10, 3))
plt.plot(result.nMarketCap, color='green')
plt.plot(result.iloc[12:, 1], color='blue')
(result.iloc[12:, 1]).plot()
plt.yticks(range(23,29))
```




    ([<matplotlib.axis.YTick at 0x2ab7c5590a0>,
      <matplotlib.axis.YTick at 0x2ab7c5557f0>,
      <matplotlib.axis.YTick at 0x2ab7c550ac0>,
      <matplotlib.axis.YTick at 0x2ab7c586280>,
      <matplotlib.axis.YTick at 0x2ab7c57ba60>,
      <matplotlib.axis.YTick at 0x2ab7c5933d0>],
     [Text(0, 0, ''),
      Text(0, 0, ''),
      Text(0, 0, ''),
      Text(0, 0, ''),
      Text(0, 0, ''),
      Text(0, 0, '')])




    
![png](output_63_1.png)
    



```python

```
