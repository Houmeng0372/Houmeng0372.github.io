# houmeng
侯萌的网站
<%@ page language="java" import="java.util.*" pageEncoding="utf-8"%>
<%@page import="util.Info"%>
<%@page import="dao.CommDAO"%>
<%@page import="util.PageManager"%>


<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
	<head>
		<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
		<title></title>


		<link rel="stylesheet" type="text/css" href="/schmsite/frontfiles/css/normalize.css" />
	<link rel="stylesheet" type="text/css" href="/schmsite/frontfiles/css/htmleaf-demo.css">
	<link rel="stylesheet" type="text/css" href="/schmsite/frontfiles/css/style.css">





		
		<style type="text/css">
<!--
#dbgdtp {
	float: left;
	margin: 0px;
	width: 960px;
}

#demo {
	overflow: hidden;
	width: 720px;
}

#demo1 {
	float: left;
}

#demo2 {
	float: left;
}

#indemo {
	float: left;
	width: 1500%;
}

-->
html,body {
	margin: 0;
	padding: 0;
}

.iw_poi_title {
	color: #CC5522;
	font-size: 14px;
	font-weight: bold;
	overflow: hidden;
	padding-right: 13px;
	white-space: nowrap
}

.iw_poi_content {
	font: 12px arial, sans-serif;
	overflow: visible;
	padding-top: 4px;
	white-space: -moz-pre-wrap;
	word-wrap: break-word
}
</style>

		<script type="text/javascript"
			src="http://api.map.baidu.com/api?key=&v=1.1&services=true"></script>
	</head>


	<body class="yanse1">


		<style>
A.applink:hover {
	border: 2px dotted #DCE6F4;
	padding: 2px;
	background-color: #ffff00;
	color: green;
	text-decoration: none
}

A.applink {
	border: 2px dotted #DCE6F4;
	padding: 2px;
	color: #2F5BFF;
	background: transparent;
	text-decoration: none
}

A.info {
	color: #2F5BFF;
	background: transparent;
	text-decoration: none
}

A.info:hover {
	color: green;
	background: transparent;
	text-decoration: underline
}
</style>





		<link href="/schmsite/frontfiles/css/css.css" rel="stylesheet"
			type="text/css" />

		<jsp:include page="top.jsp"></jsp:include>




		<table width="998" border="0" align="center" cellpadding="0"
			cellspacing="0" bgcolor="#FFFFFF">
			<tr>
				<td width="4" background="/schmsite/frontfiles/images/left.jpg">
					&nbsp;
				</td>
				<td>
					<table width="980" border="0" align="center" cellpadding="0"
						cellspacing="0">
						<tr>


<div class="htmleaf-container">








							<jsp:include page="left.jsp"></jsp:include>



							<td valign="top">
								<table width="735" border="0" align="right" cellpadding="0"
									cellspacing="0">
									<tr>
										<td height="30" valign="bottom"
											background="/schmsite/frontfiles/images/ri.jpg">
											<table width="670" border="0" align="center" cellpadding="0"
												cellspacing="0">
												<tr>
													<td align="left" class="right">
														今日推荐
													</td>
												</tr>
											</table>
										</td>
									</tr>
									<tr>
										<td valign="top"
											background="/schmsite/frontfiles/images/ri2.jpg">
											<table width="670" border="0" align="center" cellpadding="0"
												cellspacing="0" style="margin: 10px;">
												<tr>
													<td align="left" valign="top">



														<table width="100%" border="0" cellspacing="0"
															cellpadding="0">

															<tr align="center" valign="top">
																<td width="300%" colspan="3">
																	<table width="100%" border="0" cellpadding="0"
																		cellspacing="0">


																		<tr>



																			<%
                    
                    String sql = "select * from pros where status='审核'      ";
                    
                    String[] nustrs = {""};
                        String[] keys = request.getParameterValues("key")==null?nustrs:request.getParameterValues("key");
                    String key = "";
                    for(String str:keys)
                    {
                    if(str==null)str="";
                    if(str.equals(""))continue;
                    key+=str+"-";
                    }
                    
                    if(key.length()>0)key=key.substring(0,key.length()-1);
                    
                    if(key.length()>0)
                    {
                    sql+=" and ( 1=1 ";
                    for(String str:key.split("-"))
                    {
                    sql+=" and (btype like'%"+str+"%' or proname like '%"+str+"%' or stype like '%"+str+"%' ) ";
                    }
                    sql+=" ) ";
                    }
                    
                    
                    sql+="order by id desc";
                    
                     PageManager pageManager = PageManager.getPage("dzzq.jsp?1=1&key="+key, 3, request);
					  pageManager.doList(sql);
					  PageManager bean = (PageManager) request.getAttribute("page");
					  ArrayList<HashMap> nlist = (ArrayList) bean.getCollection();
                    int j=0;
                    for(HashMap mm:nlist)
                    {
                    j++;
                     %>
																			<TD vAlign=top width=33%>
																				<TABLE border=0 cellSpacing=0 cellPadding=0
																					width="100%">
																					<TBODY>
																						<TR>
																							<TD vAlign=top>
																								<TABLE border=0 cellSpacing=0 cellPadding=0
																									width="100%">
																									<TBODY>
																										<TR>
																											<TD vAlign=top>
																												<TABLE border=0 cellSpacing=0 cellPadding=0
																													width="100%">
																													<TBODY>

																														<TR>
																															<TD vAlign=top>
																																<TABLE id=standard border=0
																																	cellSpacing=1 cellPadding=0
																																	width="100%" bgColor=#EAEBE4>
																																	<TBODY>
																																		<TR>
																																			<TD height=24 align=left
																																				vAlign=center bgColor=#f7f7f7>
																																				<DIV align=center>
																																					<strong> <a
																																						href="pxiang.jsp?id=<%=mm.get("id") %>">
																																							<font color="#804000"><%=mm.get("proname") %></font>
																																					</a> </strong>
																																				</DIV>
																																				<DIV align=center></DIV>
																																			</TD>
																																		</TR>
																																		<TR>

																																			<TD width="66%" height="118"
																																				align=center vAlign=center
																																				bgColor=#ffffff>
																																				<img
																																					src="upfile/<%=mm.get("filename") %>"
																																					width="139" height="104" />
																																			</TD>
																																		</TR>
																																		<TR>
																																			<TD height="26" align=left
																																				vAlign=center bgColor=#ffffff>
																																				&nbsp;
																																			</TD>
																																		</TR>

																																		<TR>
																																			<TD width="66%" height="26"
																																				align=left vAlign=center
																																				bgColor=#ffffff>
																																				&nbsp;类别 :
																																				<%=mm.get("btype") %>
																																			</TD>
																																		</TR>
																																		<TR>
																																			<TD width="66%" height="26"
																																				align=left vAlign=center
																																				bgColor=#ffffff>
																																				&nbsp;发布时间 :
																																				<%=mm.get("savetime") %></TD>
																																		</TR>
																																	</TBODY>
																																</TABLE>
																															</TD>
																														</TR>
																													</TBODY>
																												</TABLE>
																											</TD>
																										</TR>
																									</TBODY>
																								</TABLE>
																							</TD>
																						</TR>
																					</TBODY>
																				</TABLE>
																			</TD>

																			<%
                      if(j%3!=0){
                       %>
																			<TD width=10></TD>
																			<%}else{ %>

																		</tr>

																		<tr>
																			<td height="3"></td>
																		</tr>

																		<tr>

																			<%} %>

																			<%} %>








																		</tr>

																	</table>
																</td>
															</tr>
															<tr align="center" valign="middle">
																<td height="39" colspan="3" id="page">
																	&nbsp;

																</td>
															</tr>







														</table>
													</td>
												</tr>
											</table>
										</td>
									</tr>
									<tr>
										<td height="30" valign="bottom"
											background="/schmsite/frontfiles/images/ri.jpg">
											<table width="670" border="0" align="center" cellpadding="0"
												cellspacing="0">
												<tr>
													<td align="left" class="right">
														最受欢迎
													</td>
												</tr>
											</table>
										</td>
									</tr>
									<tr>
										<td valign="top"
											background="/schmsite/frontfiles/images/ri2.jpg">
											<table width="670" border="0" align="center" cellpadding="0"
												cellspacing="0" style="margin: 10px;">
												<tr>
													<td align="left" valign="top">



														<table width="100%" border="0" cellspacing="0"
															cellpadding="0">

															<tr align="center" valign="top">
																<td width="300%" colspan="3">
																	<table width="100%" border="0" cellpadding="0"
																		cellspacing="0">


																		<tr>



																			<%
                    
                    sql = "select * from pros where status='审核'      ";
                    
                    
                      keys = request.getParameterValues("key")==null?nustrs:request.getParameterValues("key");
                     key = "";
                    for(String str:keys)
                    {
                    if(str==null)str="";
                    if(str.equals(""))continue;
                    key+=str+"-";
                    }
                    
                    if(key.length()>0)key=key.substring(0,key.length()-1);
                    
                    if(key.length()>0)
                    {
                    sql+=" and ( 1=1 ";
                    for(String str:key.split("-"))
                    {
                    sql+=" and (btype like'%"+str+"%' or proname like '%"+str+"%' or stype like '%"+str+"%' ) ";
                    }
                    sql+=" ) ";
                    }
                    
                    
                    sql+="order by id desc";
                    
                  pageManager = PageManager.getPage("dzzq.jsp?1=1&key="+key, 3, request);
					  pageManager.doList(sql);
					   bean = (PageManager) request.getAttribute("page");
					  nlist = (ArrayList) bean.getCollection();
                    j=0;
                    for(HashMap mm:nlist)
                    {
                    j++;
                     %>
																			<TD vAlign=top width=33%>
																				<TABLE border=0 cellSpacing=0 cellPadding=0
																					width="100%">
																					<TBODY>
																						<TR>
																							<TD vAlign=top>
																								<TABLE border=0 cellSpacing=0 cellPadding=0
																									width="100%">
																									<TBODY>
																										<TR>
																											<TD vAlign=top>
																												<TABLE border=0 cellSpacing=0 cellPadding=0
																													width="100%">
																													<TBODY>

																														<TR>
																															<TD vAlign=top>
																																<TABLE id=standard border=0
																																	cellSpacing=1 cellPadding=0
																																	width="100%" bgColor=#EAEBE4>
																																	<TBODY>
																																		<TR>
																																			<TD height=24 align=left
																																				vAlign=center bgColor=#f7f7f7>
																																				<DIV align=center>
																																					<strong> <a
																																						href="pxiang.jsp?id=<%=mm.get("id") %>">
																																							<font color="#804000"><%=mm.get("proname") %></font>
																																					</a> </strong>
																																				</DIV>
																																				<DIV align=center></DIV>
																																			</TD>
																																		</TR>
																																		<TR>

																																			<TD width="66%" height="118"
																																				align=center vAlign=center
																																				bgColor=#ffffff>
																																				<img
																																					src="upfile/<%=mm.get("filename") %>"
																																					width="139" height="104" />
																																			</TD>
																																		</TR>


																																		<TR>
																																			<TD width="66%" height="26"
																																				align=left vAlign=center
																																				bgColor=#ffffff>
																																				&nbsp;类别 :
																																				<%=mm.get("btype") %>
																																			</TD>
																																		</TR>
																																		<TR>
																																			<TD width="66%" height="26"
																																				align=left vAlign=center
																																				bgColor=#ffffff>
																																				&nbsp;发布时间 :
																																				<%=mm.get("savetime") %></TD>
																																		</TR>
																																	</TBODY>
																																</TABLE>
																															</TD>
																														</TR>
																													</TBODY>
																												</TABLE>
																											</TD>
																										</TR>
																									</TBODY>
																								</TABLE>
																							</TD>
																						</TR>
																					</TBODY>
																				</TABLE>
																			</TD>

																			<%
                      if(j%3!=0){
                       %>
																			<TD width=10></TD>
																			<%}else{ %>

																		</tr>

																		<tr>
																			<td height="3"></td>
																		</tr>

																		<tr>

																			<%} %>

																			<%} %>








																		</tr>

																	</table>
																</td>
															</tr>
															<tr align="center" valign="middle">
																<td height="39" colspan="3" id="page">
																	&nbsp;

																</td>
															</tr>







														</table>
													</td>
												</tr>
											</table>
										</td>
									</tr>
									<tr>
										<td height="30" valign="bottom"
											background="/schmsite/frontfiles/images/ri.jpg">
											<table width="670" border="0" align="center" cellpadding="0"
												cellspacing="0">
												<tr>
													<td align="left" class="right">
														今日排行
													</td>
												</tr>
											</table>
										</td>
									</tr>
									<tr>
										<td valign="top"
											background="/schmsite/frontfiles/images/ri2.jpg">
											<table width="670" border="0" align="center" cellpadding="0"
												cellspacing="0" style="margin: 10px;">
												<tr>
													<td align="left" valign="top">



														<table width="100%" border="0" cellspacing="0"
															cellpadding="0">

															<tr align="center" valign="top">
																<td width="300%" colspan="3">
																	<table width="100%" border="0" cellpadding="0"
																		cellspacing="0">


																		<tr>



																			<%
                    
                     sql = "select * from pros where status='审核'      ";
                    
                  
                         keys = request.getParameterValues("key")==null?nustrs:request.getParameterValues("key");
                      key = "";
                    for(String str:keys)
                    {
                    if(str==null)str="";
                    if(str.equals(""))continue;
                    key+=str+"-";
                    }
                    
                    if(key.length()>0)key=key.substring(0,key.length()-1);
                    
                    if(key.length()>0)
                    {
                    sql+=" and ( 1=1 ";
                    for(String str:key.split("-"))
                    {
                    sql+=" and (btype like'%"+str+"%' or proname like '%"+str+"%' or stype like '%"+str+"%' ) ";
                    }
                    sql+=" ) ";
                    }
                    
                    
                    sql+="order by id desc";
                    
                      pageManager = PageManager.getPage("dzzq.jsp?1=1&key="+key, 3, request);
					  pageManager.doList(sql);
					    bean = (PageManager) request.getAttribute("page");
					  nlist = (ArrayList) bean.getCollection();
                      j=0;
                    for(HashMap mm:nlist)
                    {
                    j++;
                     %>
																			<TD vAlign=top width=33%>
																				<TABLE border=0 cellSpacing=0 cellPadding=0
																					width="100%">
																					<TBODY>
																						<TR>
																							<TD vAlign=top>
																								<TABLE border=0 cellSpacing=0 cellPadding=0
																									width="100%">
																									<TBODY>
																										<TR>
																											<TD vAlign=top>
																												<TABLE border=0 cellSpacing=0 cellPadding=0
																													width="100%">
																													<TBODY>

																														<TR>
																															<TD vAlign=top>
																																<TABLE id=standard border=0
																																	cellSpacing=1 cellPadding=0
																																	width="100%" bgColor=#EAEBE4>
																																	<TBODY>
																																		<TR>
																																			<TD height=24 align=left
																																				vAlign=center bgColor=#f7f7f7>
																																				<DIV align=center>
																																					<strong> <a
																																						href="pxiang.jsp?id=<%=mm.get("id") %>">
																																							<font color="#804000"><%=mm.get("proname") %></font>
																																					</a> </strong>
																																				</DIV>
																																				<DIV align=center></DIV>
																																			</TD>
																																		</TR>
																																		<TR>

																																			<TD width="66%" height="118"
																																				align=center vAlign=center
																																				bgColor=#ffffff>
																																				<img
																																					src="upfile/<%=mm.get("filename") %>"
																																					width="139" height="104" />
																																			</TD>
																																		</TR>


																																		<TR>
																																			<TD width="66%" height="26"
																																				align=left vAlign=center
																																				bgColor=#ffffff>
																																				&nbsp;类别 :
																																				<%=mm.get("btype") %>
																																			</TD>
																																		</TR>
																																		<TR>
																																			<TD width="66%" height="26"
																																				align=left vAlign=center
																																				bgColor=#ffffff>
																																				&nbsp;发布时间 :
																																				<%=mm.get("savetime") %></TD>
																																		</TR>
																																	</TBODY>
																																</TABLE>
																															</TD>
																														</TR>
																													</TBODY>
																												</TABLE>
																											</TD>
																										</TR>
																									</TBODY>
																								</TABLE>
																							</TD>
																						</TR>
																					</TBODY>
																				</TABLE>
																			</TD>

																			<%
                      if(j%3!=0){
                       %>
																			<TD width=10></TD>
																			<%}else{ %>

																		</tr>

																		<tr>
																			<td height="3"></td>
																		</tr>

																		<tr>

																			<%} %>

																			<%} %>








																		</tr>

																	</table>
																</td>
															</tr>
															<tr align="center" valign="middle">
																<td height="39" colspan="3" id="page">
																	&nbsp;

																</td>
															</tr>







														</table>
													</td>
												</tr>
											</table>
										</td>
									</tr>
									<tr>
										<td>
											<img src="/schmsite/frontfiles/images/ri1.jpg" width="735"
												height="15" />
										</td>
									</tr>
								</table>
							</td>
						</tr>
					</table>
				</td>
				<td width="4" background="/schmsite/frontfiles/images/right.jpg">
					&nbsp;
				</td>
			</tr>
		</table>



		<link href="css/css.css" rel="stylesheet" type="text/css" />

		<jsp:include page="foot.jsp"></jsp:include>













		<!--百度地图容器-->
		<div style="width: 300px; height: 250px; border: #ccc solid 1px;"
			id="dituContent"></div>



	</body>
</html>
<script language=javascript
	src='/schmsite/js/My97DatePicker/WdatePicker.js'></script>
<script language=javascript src='/schmsite/js/popup.js'></script>
<script language=javascript src='/schmsite/js/ajax.js'></script>
<%@page import="util.Info"%>
<%@page import="util.Info"%>
<%@page import="java.util.ArrayList"%>
<%@page import="java.util.HashMap"%>
<%@page import="util.PageManager"%>
<%@page import="dao.CommDAO"%>
<script language=javascript>  
 
 function checkform(){  
var unameobj = document.getElementById("uname");  
if(unameobj.value==""){  
document.getElementById("clabeluname").innerHTML="&nbsp;&nbsp;<font color=red>请输入用户名</font>";  
return false;  
}else{
document.getElementById("clabeluname").innerHTML="  ";  
}  
  
var unameobj = document.getElementById("uname");  
if(unameobj.value!=""){  
var ajax = new AJAX();
ajax.post("/schmsite/factory/checkno.jsp?table=sysuser&col=uname&value="+unameobj.value+"&checktype=insert&ttime=<%=Info.getDateStr()%>") 
var msg = ajax.getValue();
if(msg.indexOf('Y')>-1){
document.getElementById("clabeluname").innerHTML="&nbsp;&nbsp;<font color=red>用户名已存在</font>";  
return false;
}else{document.getElementById("clabeluname").innerHTML="  ";  
}  
}  
var upassobj = document.getElementById("upass");  
if(upassobj.value==""){  
document.getElementById("clabelupass").innerHTML="&nbsp;&nbsp;<font color=red>请输入密码</font>";  
return false;  
}else{
document.getElementById("clabelupass").innerHTML="  ";  
}  
  
var tnameobj = document.getElementById("tname");  
if(tnameobj.value==""){  
document.getElementById("clabeltname").innerHTML="&nbsp;&nbsp;<font color=red>请输入姓名</font>";  
return false;  
}else{
document.getElementById("clabeltname").innerHTML="  ";  
}  
  
var telobj = document.getElementById("tel");  
if(telobj.value!=""){  
if(telobj.value.length>11||telobj.value.length<8||isNaN(telobj.value)){ 
document.getElementById("clabeltel").innerHTML="&nbsp;&nbsp;<font color=red>联系电话必须为8-11位数字</font>";  
return false;
}else{  
document.getElementById("clabeltel").innerHTML="";  
}  
}  
var qqobj = document.getElementById("qq");  
if(qqobj.value!=""){  
if(qqobj.value.length>12||isNaN(qqobj.value)){ 
document.getElementById("clabelqq").innerHTML="&nbsp;&nbsp;<font color=red>联系QQ必须为12位以内数字</font>";  
return false;
}else{  
document.getElementById("clabelqq").innerHTML="";  
}  
}  
return true;   
}   
popheight=450;






 //创建和初始化地图函数：
    function initMap(){
        createMap();//创建地图
        setMapEvent();//设置地图事件
        addMapControl();//向地图添加控件
        addMarker();//向地图中添加marker
    }
    
    //创建地图函数：
    function createMap(){
        var map = new BMap.Map("dituContent");//在百度地图容器中创建一个地图
        var point = new BMap.Point(113.947845,35.297468);//定义一个中心点坐标
        map.centerAndZoom(point,18);//设定地图的中心点和坐标并将地图显示在地图容器中
        window.map = map;//将map变量存储在全局
    }
    
    //地图事件设置函数：
    function setMapEvent(){
        map.enableDragging();//启用地图拖拽事件，默认启用(可不写)
        map.enableScrollWheelZoom();//启用地图滚轮放大缩小
        map.enableDoubleClickZoom();//启用鼠标双击放大，默认启用(可不写)
        map.enableKeyboard();//启用键盘上下左右键移动地图
    }
    
    //地图控件添加函数：
    function addMapControl(){
        //向地图中添加缩放控件
	var ctrl_nav = new BMap.NavigationControl({anchor:BMAP_ANCHOR_TOP_LEFT,type:BMAP_NAVIGATION_CONTROL_PAN});
	map.addControl(ctrl_nav);
        //向地图中添加缩略图控件
	var ctrl_ove = new BMap.OverviewMapControl({anchor:BMAP_ANCHOR_BOTTOM_RIGHT,isOpen:1});
	map.addControl(ctrl_ove);
        //向地图中添加比例尺控件
	var ctrl_sca = new BMap.ScaleControl({anchor:BMAP_ANCHOR_BOTTOM_LEFT});
	map.addControl(ctrl_sca);
    }
    
    //标注点数组
    var markerArr = [{title:"新乡学院漫画网公司",content:"新乡学院",point:"113.947953|35.297351",isOpen:0,icon:{w:21,h:21,l:0,t:0,x:6,lb:5}}
		 ];
    //创建marker
    function addMarker(){
        for(var i=0;i<markerArr.length;i++){
            var json = markerArr[i];
            var p0 = json.point.split("|")[0];
            var p1 = json.point.split("|")[1];
            var point = new BMap.Point(p0,p1);
			var iconImg = createIcon(json.icon);
            var marker = new BMap.Marker(point,{icon:iconImg});
			var iw = createInfoWindow(i);
			var label = new BMap.Label(json.title,{"offset":new BMap.Size(json.icon.lb-json.icon.x+10,-20)});
			marker.setLabel(label);
            map.addOverlay(marker);
            label.setStyle({
                        borderColor:"#808080",
                        color:"#333",
                        cursor:"pointer"
            });
			
			(function(){
				var index = i;
				var _iw = createInfoWindow(i);
				var _marker = marker;
				_marker.addEventListener("click",function(){
				    this.openInfoWindow(_iw);
			    });
			    _iw.addEventListener("open",function(){
				    _marker.getLabel().hide();
			    })
			    _iw.addEventListener("close",function(){
				    _marker.getLabel().show();
			    })
				label.addEventListener("click",function(){
				    _marker.openInfoWindow(_iw);
			    })
				if(!!json.isOpen){
					label.hide();
					_marker.openInfoWindow(_iw);
				}
			})()
        }
    }
    //创建InfoWindow
    function createInfoWindow(i){
        var json = markerArr[i];
        var iw = new BMap.InfoWindow("<b class='iw_poi_title' title='" + json.title + "'>" + json.title + "</b><div class='iw_poi_content'>"+json.content+"</div>");
        return iw;
    }
    //创建一个Icon
    function createIcon(json){
        var icon = new BMap.Icon("http://app.baidu.com/map/images/us_mk_icon.png", new BMap.Size(json.w,json.h),{imageOffset: new BMap.Size(-json.l,-json.t),infoWindowOffset:new BMap.Size(json.lb+5,1),offset:new BMap.Size(json.x,json.h)})
        return icon;
    }
    
    initMap();//创建和初始化地图
</script>
