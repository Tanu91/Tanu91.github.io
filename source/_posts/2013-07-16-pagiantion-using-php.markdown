---
layout: post
title: "Pagiantion using PHP"
date: 2013-07-16 20:58
comments: true
categories: 
---

Script used for pagianation 
{% codeblock %}<?php
include 'connect.php';  # Include your Database connection script
$per_page = 10;  # No. of rows to be displyed per page
$pages_query= mysql_query("SELECT COUNT(*) FROM Table_Name"); # Count the total number of rows In table
$pages=ceil(mysql_result($pages_query,0)/$per_page);
$page = (isset($_GET['page'])) ? (int)$_GET['page'] : 1;  #to set default page as 1
$start = ($page - 1) * $per_page;   # Resolving for next rows to be displayed per page
$query = mysql_query("SELECT Column_Names from Table_name LIMIT $start, $per_page");  # limit the number of rows to be displyed per-page
while ($row = mysql_fetch_assoc($query)) {
 echo "$row['column_name'];    # echo values
		echo "<br>";
	}
if($pages>=1 && $page<=$pages){   
for($x=1; $x<=$pages ;$x++){
echo ($x == $page) ? '<strong><a href="?page='.$x.'">'.$x.'</a> </strong>' : '<a href="?page='.$x.'">'.$x.'</a> ';  # Visualize current link strong
   }
}
?>
{% endcodeblock %}
