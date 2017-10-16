---
layout: post
title:  "MẬT MÃ CAESAR"
date:   2016-09-17 13:50:29
categories: antoanbaomat
---
<h1>Mô phỏng mật mã Caesar qua C++</h1>
<hr>
<table class="highlight tab-size js-file-line-container" data-tab-size="8">
<tbody>
<tr>
<td id="LC2" class="blob-code blob-code-inner js-file-line">#<span class="pl-k">include</span> <span class="pl-s"><span class="pl-pds">&lt;</span>iostream<span class="pl-pds">&gt;</span></span></td>
</tr>
<tr>
<td id="L3" class="blob-num js-line-number" data-line-number="3">&nbsp;</td>
<td id="LC3" class="blob-code blob-code-inner js-file-line">#<span class="pl-k">include</span> <span class="pl-s"><span class="pl-pds">&lt;</span>string<span class="pl-pds">&gt;</span></span></td>
</tr>
<tr>
<td id="L4" class="blob-num js-line-number" data-line-number="4">&nbsp;</td>
<td id="LC4" class="blob-code blob-code-inner js-file-line">#<span class="pl-k">include</span><span class="pl-s"><span class="pl-pds">&lt;</span>stdlib.h<span class="pl-pds">&gt;</span></span></td>
</tr>
<tr>
<td id="L5" class="blob-num js-line-number" data-line-number="5">&nbsp;</td>
<td id="LC5" class="blob-code blob-code-inner js-file-line"><span class="pl-k">using</span> <span class="pl-k">namespace</span> <span class="pl-en">std</span><span class="pl-k">;</span></td>
</tr>
<tr>
<td id="L6" class="blob-num js-line-number" data-line-number="6">&nbsp;</td>
<td id="LC6" class="blob-code blob-code-inner js-file-line"><span class="pl-c">//Mật m&atilde; CAESAR</span></td>
</tr>
<tr>
<td id="L7" class="blob-num js-line-number" data-line-number="7">&nbsp;</td>
<td id="LC7" class="blob-code blob-code-inner js-file-line"><span class="pl-k">char</span> Plaintext[] ={<span class="pl-s"><span class="pl-pds">'</span>a<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>b<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>c<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>d<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>e<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>f<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>g<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>h<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>i<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>j<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>k<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>l<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>m<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>n<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>o<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>p<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>q<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>r<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>s<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>t<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>u<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>v<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>w<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>x<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>y<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>z<span class="pl-pds">'</span></span>};</td>
</tr>
<tr>
<td id="L8" class="blob-num js-line-number" data-line-number="8">&nbsp;</td>
<td id="LC8" class="blob-code blob-code-inner js-file-line"><span class="pl-k">char</span> Ciphertext[] ={<span class="pl-s"><span class="pl-pds">'</span>d<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>e<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>f<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>g<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>h<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>i<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>j<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>k<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>l<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>m<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>n<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>o<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>p<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>q<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>r<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>s<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>t<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>u<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>v<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>w<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>x<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>y<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>z<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>a<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>b<span class="pl-pds">'</span></span>,<span class="pl-s"><span class="pl-pds">'</span>c<span class="pl-pds">'</span></span>};</td>
</tr>
<tr>
<td id="L9" class="blob-num js-line-number" data-line-number="9">&nbsp;</td>
<td id="LC9" class="blob-code blob-code-inner js-file-line"><span class="pl-k">int</span> <span class="pl-en">number_to_char</span>(<span class="pl-k">char</span> text)</td>
</tr>
<tr>
<td id="L10" class="blob-num js-line-number" data-line-number="10">&nbsp;</td>
<td id="LC10" class="blob-code blob-code-inner js-file-line">{</td>
</tr>
<tr>
<td id="L11" class="blob-num js-line-number" data-line-number="11">&nbsp;</td>
<td id="LC11" class="blob-code blob-code-inner js-file-line"><span class="pl-k">for</span>(<span class="pl-k">int</span> i=<span class="pl-c1">0</span>;i&lt;<span class="pl-c1">26</span>;i++)</td>
</tr>
<tr>
<td id="L12" class="blob-num js-line-number" data-line-number="12">&nbsp;</td>
<td id="LC12" class="blob-code blob-code-inner js-file-line">{</td>
</tr>
<tr>
<td id="L13" class="blob-num js-line-number" data-line-number="13">&nbsp;</td>
<td id="LC13" class="blob-code blob-code-inner js-file-line"><span class="pl-k">if</span>(Plaintext[i]==text) <span class="pl-k">return</span> i;</td>
</tr>
<tr>
<td id="L14" class="blob-num js-line-number" data-line-number="14">&nbsp;</td>
<td id="LC14" class="blob-code blob-code-inner js-file-line">}</td>
</tr>
<tr>
<td id="L15" class="blob-num js-line-number" data-line-number="15">&nbsp;</td>
<td id="LC15" class="blob-code blob-code-inner js-file-line">}</td>
</tr>
<tr>
<td id="L16" class="blob-num js-line-number" data-line-number="16">&nbsp;</td>
<td id="LC16" class="blob-code blob-code-inner js-file-line"><span class="pl-k">char</span> <span class="pl-en">number_to_char</span>(<span class="pl-k">int</span> i)</td>
</tr>
<tr>
<td id="L17" class="blob-num js-line-number" data-line-number="17">&nbsp;</td>
<td id="LC17" class="blob-code blob-code-inner js-file-line">{</td>
</tr>
<tr>
<td id="L18" class="blob-num js-line-number" data-line-number="18">&nbsp;</td>
<td id="LC18" class="blob-code blob-code-inner js-file-line"><span class="pl-k">return</span> Ciphertext[i];</td>
</tr>
<tr>
<td id="L19" class="blob-num js-line-number" data-line-number="19">&nbsp;</td>
<td id="LC19" class="blob-code blob-code-inner js-file-line">}</td>
</tr>
<tr>
<td id="L20" class="blob-num js-line-number" data-line-number="20">&nbsp;</td>
<td id="LC20" class="blob-code blob-code-inner js-file-line"><span class="pl-k">int</span> <span class="pl-en">main</span>() {</td>
</tr>
<tr>
<td id="L21" class="blob-num js-line-number" data-line-number="21">&nbsp;</td>
<td id="LC21" class="blob-code blob-code-inner js-file-line">string chuoi,mahoa,giaima;</td>
</tr>
<tr>
<td id="L22" class="blob-num js-line-number" data-line-number="22">&nbsp;</td>
<td id="LC22" class="blob-code blob-code-inner js-file-line"><span class="pl-k">int</span> k=<span class="pl-c1">3</span>;</td>
</tr>
<tr>
<td id="L23" class="blob-num js-line-number" data-line-number="23">&nbsp;</td>
<td id="LC23" class="blob-code blob-code-inner js-file-line">cout&lt;&lt;<span class="pl-s"><span class="pl-pds">"</span>Mời bạn nhập chuỗi đầu v&agrave;o: <span class="pl-pds">"</span></span>&lt;&lt;endl;</td>
</tr>
<tr>
<td id="L24" class="blob-num js-line-number" data-line-number="24">&nbsp;</td>
<td id="LC24" class="blob-code blob-code-inner js-file-line"><span class="pl-c1">getline</span>(cin,chuoi);</td>
</tr>
<tr>
<td id="L25" class="blob-num js-line-number" data-line-number="25">&nbsp;</td>
<td id="LC25" class="blob-code blob-code-inner js-file-line">mahoa=chuoi;</td>
</tr>
<tr>
<td id="L26" class="blob-num js-line-number" data-line-number="26">&nbsp;</td>
<td id="LC26" class="blob-code blob-code-inner js-file-line"><span class="pl-k">for</span>(<span class="pl-k">int</span> i=<span class="pl-c1">0</span>;i&lt;chuoi.<span class="pl-c1">size</span>();i++)</td>
</tr>
<tr>
<td id="L27" class="blob-num js-line-number" data-line-number="27">&nbsp;</td>
<td id="LC27" class="blob-code blob-code-inner js-file-line">{</td>
</tr>
<tr>
<td id="L28" class="blob-num js-line-number" data-line-number="28">&nbsp;</td>
<td id="LC28" class="blob-code blob-code-inner js-file-line">mahoa[i]=<span class="pl-c1">number_to_char</span>((<span class="pl-c1">number_to_char</span>(chuoi[i])+k)%<span class="pl-c1">26</span>);</td>
</tr>
<tr>
<td id="L29" class="blob-num js-line-number" data-line-number="29">&nbsp;</td>
<td id="LC29" class="blob-code blob-code-inner js-file-line">}</td>
</tr>
<tr>
<td id="L30" class="blob-num js-line-number" data-line-number="30">&nbsp;</td>
<td id="LC30" class="blob-code blob-code-inner js-file-line">cout&lt;&lt;<span class="pl-s"><span class="pl-pds">"</span>Chuỗi sau khi m&atilde; h&oacute;a: <span class="pl-pds">"</span></span>&lt;&lt;mahoa&lt;&lt;endl;</td>
</tr>
<tr>
<td id="L31" class="blob-num js-line-number" data-line-number="31">&nbsp;</td>
<td id="LC31" class="blob-code blob-code-inner js-file-line">&nbsp;</td>
</tr>
<tr>
<td id="L32" class="blob-num js-line-number" data-line-number="32">&nbsp;</td>
<td id="LC32" class="blob-code blob-code-inner js-file-line">giaima=mahoa;</td>
</tr>
<tr>
<td id="L33" class="blob-num js-line-number" data-line-number="33">&nbsp;</td>
<td id="LC33" class="blob-code blob-code-inner js-file-line"><span class="pl-k">for</span>(<span class="pl-k">int</span> i=<span class="pl-c1">0</span>;i&lt;mahoa.<span class="pl-c1">size</span>();i++)</td>
</tr>
<tr>
<td id="L34" class="blob-num js-line-number" data-line-number="34">&nbsp;</td>
<td id="LC34" class="blob-code blob-code-inner js-file-line">{</td>
</tr>
<tr>
<td id="L35" class="blob-num js-line-number" data-line-number="35">&nbsp;</td>
<td id="LC35" class="blob-code blob-code-inner js-file-line">giaima[i]=<span class="pl-c1">number_to_char</span>((<span class="pl-c1">number_to_char</span>(chuoi[i])-k+<span class="pl-c1">26</span>)%<span class="pl-c1">26</span>);</td>
</tr>
<tr>
<td id="L36" class="blob-num js-line-number" data-line-number="36">&nbsp;</td>
<td id="LC36" class="blob-code blob-code-inner js-file-line">}</td>
</tr>
<tr>
<td id="L37" class="blob-num js-line-number" data-line-number="37">&nbsp;</td>
<td id="LC37" class="blob-code blob-code-inner js-file-line">cout&lt;&lt;<span class="pl-s"><span class="pl-pds">"</span>Chuỗi sau khi giải m&atilde;: <span class="pl-pds">"</span></span>&lt;&lt;giaima&lt;&lt;endl;</td>
</tr>
<tr>
<td id="L38" class="blob-num js-line-number" data-line-number="38">&nbsp;</td>
<td id="LC38" class="blob-code blob-code-inner js-file-line"><span class="pl-k">return</span> <span class="pl-c1">0</span>;</td>
</tr>
<tr>
<td id="L39" class="blob-num js-line-number" data-line-number="39">&nbsp;</td>
<td id="LC39" class="blob-code blob-code-inner js-file-line">}</td>
</tr>
</tbody>
</table>
