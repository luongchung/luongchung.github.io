---
layout: post
title:  " CƠ BẢN LINQ TO SQL SERVER -C#"
date:   2017-09-17 13:50:29
categories: other
---
<p><strong>#1: Lấy tất cả bản ghi của bảng khoa:</strong></p>
<p><em>var data = from a in db.khoa select new {a.Ma_Khoa,a.TenKhoa};</em></p>
<p><strong>#2: Lấy tất cả bản ghi của bảng khoa với điều kiện m&atilde; khoa=1:</strong></p>
<p><em>var data = from a in db.khoa where a.Ma_Khoa==1 select new {a.Ma_Khoa,a.TenKhoa};</em></p>
<p><strong>#3: Lấy tất cả bản ghi của bảng khoa với điều kiện t&ecirc;n khoa bắt đầu bằng chữ T:</strong></p>
<p><em>var data = from a in db.khoa where a.Ma_Khoa.StartsWith(&ldquo;T&rdquo;) &nbsp;select new {a.Ma_Khoa,a.TenKhoa};</em></p>
<p><strong>#4: Lấy tất cả bản ghi của bảng khoa sắp xếp theo t&ecirc;n khoa:</strong></p>
<p><em>var data = from a in db.khoa orderby sv.Ten_Khoa descending</em></p>
<p><em>select new {a.Ma_Khoa,a.TenKhoa};</em></p>
<p><em>&nbsp;</em></p>
<p><em>note: descending l&agrave; giảm dần, bỏ đi l&agrave; tăng.</em></p>
<p><strong>#5: Join bảng khoa với sinh vi&ecirc;n bằng m&atilde; khoa:</strong></p>
<p><em>var data = from k in db.khoa </em></p>
<p><em>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; join sv in db.SinhVien on k.Ma_Khoa equal sv.Ma_khoa</em></p>
<p><em>select new {sv.TenSV,k.TenKhoa};</em></p>
<p><em>&nbsp;</em></p>
<p><em>&nbsp;</em></p>
<p><em>&nbsp;</em></p>
<p><strong>#6: Lấy tất cả bản ghi bảng sinh vi&ecirc;n c&oacute; thuộc bảng khoa:</strong></p>
<p><em>var data = from sv in db.SinhVien</em></p>
<p><em>where (from k in db.khoa select k.MaKhoa).Contains(sv.MaKhoa) </em></p>
<p><em>select new {sv.TenSV };</em></p>
<p><strong>#7: Lấy tất cả bản ghi bảng sinh vi&ecirc;n m&agrave; kh&ocirc;ng thuộc bảng khoa:</strong></p>
<p><em>var data = from sv in db.SinhVien</em></p>
<p><em>where !(from k in db.khoa select k.MaKhoa).Contains(sv.MaKhoa) </em></p>
<p><em>select new {sv.TenSV };</em></p>
<p><em>&nbsp;</em></p>
<p><strong>#8:Lấy ra sinh vi&ecirc;n chưa c&oacute; khoa v&agrave; c&oacute; khoa, nếu null chưa c&oacute; khoa để l&agrave; &ldquo;Chưa c&oacute;&rdquo;:</strong></p>
<p><em>var data = from sv in db.SinhVien</em></p>
<p><em>join k in db.khoa on k.Ma_Khoa equal sv.Ma_khoa into tmp from p in tmp.DefaulIfEmpty()</em></p>
<p><em>select new {sv.TenSV,TenKhoa=(p==null)?&rdquo;Chưa c&oacute;&rdquo;:p.TenKhoa };</em></p>
<p><strong>#9:Lấy ra số sinh vi&ecirc;n của từng khoa, v&agrave; học bổng của sv cao nhất của khoa đấy:</strong></p>
<p><em>var data = from k in db.Khoa</em></p>
<p><em>join sv in db.SinhVien on k.MaKhoa==sv.MaKhoa</em></p>
<p><em>group sv by new {k.MaKhoa} into tmp</em></p>
<p><em>select new {tmp.Key.TenKhoa,SoSinhVien=tmp.count(),HoBongMax=tmp.max(p=&gt;p.HocBong) };</em></p>
<p><strong>#10:Lấy ra 5 bản ghi đầu ti&ecirc;n:</strong></p>
<p><em>var data =( from a in db.khoa select new {a.Ma_Khoa,a.TenKhoa}).Skip(0).Take(5);</em></p>
<p><em>&nbsp;</em></p>
<p><em>Note: Lấy ra 5 bản ghi bắt đầu từ bản ghi 0 , skip(3) c&oacute; nghĩa bỏ qua 3 bản ghi.</em></p>