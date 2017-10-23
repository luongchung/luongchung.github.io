---
layout: post
title:  "MÃ HÓA HOÁN VỊ DỊCH CHUYỂN"
date:   2016-09-17 13:50:29
categories: antoanbaomat
---
<h1>Mã hóa hoán vị dịch chuyển</h1>
<hr?
<div>#include &lt;iostream&gt;</div>
<div>#include &lt;string&gt;</div>
<div>#include&lt;stdlib.h&gt;</div>
<div>using namespace std;</div>
<div>int main() {</div>
<div>string chuoi,chuoimh,chuoigm;</div>
<div>char arr[5][5];</div>
<div>char arr1[5][5];</div>
<div>cout&lt;&lt;"Mời bạn nhập chuỗi: "&lt;&lt;endl;</div>
<div>&nbsp;</div>
<div>chuoi="CONGHOAXAHOICHUNGHIAVIETNAM";</div>
<div>&nbsp;</div>
<div>//M&Atilde; H&Oacute;A</div>
<div>&nbsp;</div>
<div>int u=0;</div>
<div>for(int i=0;i&lt;5;i++)</div>
<div>{</div>
<div>for (int j=0;j&lt;5;j++)</div>
<div>{</div>
<div>arr[i][j]=chuoi[u];</div>
<div>u++;</div>
<div>cout&lt;&lt;arr[i][j]&lt;&lt;" ";</div>
<div>}</div>
<div>cout&lt;&lt;endl;</div>
<div>}</div>
<div>cout&lt;&lt;"Chuỗi sau khi m&atilde; h&oacute;a: ";</div>
<div>for(int i=0;i&lt;5;i++)</div>
<div>{</div>
<div>for (int j=0;j&lt;5;j++)</div>
<div>{</div>
<div>chuoimh.push_back(arr[j][i]);</div>
<div>}</div>
<div>}</div>
<div>cout&lt;&lt;endl&lt;&lt;chuoimh&lt;&lt;endl;</div>
<div>&nbsp;</div>
<div>//GIẢI M&Atilde;.</div>
<div>u=0;</div>
<div>for(int i=0;i&lt;5;i++)</div>
<div>{</div>
<div>for (int j=0;j&lt;5;j++)</div>
<div>{</div>
<div>arr1[i][j]=chuoimh[u];</div>
<div>cout&lt;&lt;arr1[i][j]&lt;&lt;" ";</div>
<div>u++;</div>
<div>}</div>
<div>cout&lt;&lt;endl;</div>
<div>}</div>
<div>&nbsp;</div>
<div>for(int i=0;i&lt;5;i++)</div>
<div>{</div>
<div>for (int j=0;j&lt;5;j++)</div>
<div>{</div>
<div>chuoigm.push_back(arr1[j][i]);</div>
<div>}</div>
<div>&nbsp;</div>
<div>}</div>
<div>cout&lt;&lt;"Chuoi sau khi giải m&atilde;: "&lt;&lt;endl&lt;&lt;chuoigm;</div>
<div>&nbsp;</div>
<div>return 0;</div>
<div>}</div>
