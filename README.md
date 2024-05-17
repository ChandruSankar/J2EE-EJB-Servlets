# J2EE-EJB-Servlets
This repository contains the source code of all the Servlets, EJBs created during the J2EE Training
---
## **Notes:**

J2SE->Core->void main
J2ME->Micro
J2EE->Enterprise->Container[Service which hosts web apps]
war container
Container:
Web server(Rest,SOAP,JSP,Servlets,Restlets)[Tomcat]
Application Server(Rest,SOAP,JSP,Servlets,Restlets,EJB)
[Websphere,Weblogic,Apache geronimo, Glassfish, JBOSS,Resin]
Distributed apps

Three modes of distribution of java apps
jar->java archive
war->Web archive(Rest,SOAP,JSP,Servlets,Restlets,EJB)
ear->Enterprise archive(EJB)

Standalone and Domain(Calling a ejb will have considerable changes(JNDI))


package co.cls.mods;

public class Cars {
	private int cid;

	public int getCid() {
		return cid;
	}

	public void setCid(int cid) {
		this.cid = cid;
	}

	public String getCname() {
		return cname;
	}

	public void setCname(String cname) {
		this.cname = cname;
	}

	public String getCbrand() {
		return cbrand;
	}

	public void setCbrand(String cbrand) {
		this.cbrand = cbrand;
	}

	private String cname;
	private String cbrand;
}
/////////
package co.cls.st;

import java.io.IOException;
import java.io.PrintWriter;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

/**
 * Servlet implementation class BServe
 */
@WebServlet("/BServe")
public class BServe extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public BServe() {
        super();
        // TODO Auto-generated constructor stub
    }

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		PrintWriter out=response.getWriter();
		out.println("<h1 style=\"background-color:red;color:yellow\">Second Servlet Running</h1>");
	}

	/**
	 * @see HttpServlet#doPost(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		doGet(request, response);
	}

}
///////
package co.cls.mods;

import java.util.ArrayList;
import java.util.List;

public class ListCars {
		public List<Cars> retCList(){
			List<Cars> lc=new ArrayList<Cars>();
			int[] arr1= {101,201,301,401,501};
			String[] arr2= {"Octavio","Thar","Empala","Camry","ECclass"};
			String[] arr3= {"Skoda","Jeep","Ambassador","Toyota","Mercedes"};
			for (int i = 0; i < arr3.length; i++) {
				Cars c=new Cars();
				c.setCid(arr1[i]);
				c.setCname(arr2[i]);
				c.setCbrand(arr3[i]);
				lc.add(c);
			}
			return lc;
		}
}
///////
package co.cls.st;

import java.io.IOException;
import java.io.PrintWriter;
import java.util.List;
import java.util.function.Consumer;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import co.cls.mods.Cars;
import co.cls.mods.ListCars;

/**
 * Servlet implementation class Index
 */
@WebServlet("/Index")
public class Index extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public Index() {
        super();
        // TODO Auto-generated constructor stub
    }

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		PrintWriter out=response.getWriter();
		List<Cars> lc=null;
		ListCars lcObj=new ListCars();
		lc=lcObj.retCList();
		String disp="<center><table border=1><thead><tr><th>Car ID</th><th>Car Name</th><th>Car Brand</th></tr></thead><tbody>";
		for(Cars c:lc) {
			disp+="<tr><td>"+c.getCid()+"</td><td>"+c.getCname()+"</td><td>"+c.getCbrand()+"</td></tr>";
		}
		disp+="</tbody></table><center>";
		out.println("<center><h1>Welcome to car show room we have following cars for display</h1></center><br/><hr/><br/>");
		out.println(disp);
	}

	/**
	 * @see HttpServlet#doPost(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		doGet(request, response);
	}

}
////////
package co.cls.st;

import java.io.IOException;
import java.io.PrintWriter;
import java.util.List;
import java.util.function.Consumer;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import co.cls.mods.Cars;
import co.cls.mods.ListCars;

/**
 * Servlet implementation class Index
 */
@WebServlet("/Index")
public class Index extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public Index() {
        super();
        // TODO Auto-generated constructor stub
    }

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		PrintWriter out=response.getWriter();
		List<Cars> lc=null;
		ListCars lcObj=new ListCars();
		lc=lcObj.retCList();
		String disp="<center><table border=1 style=\"background-color:black;color:yellow;\"><thead><tr><th>Car ID</th><th>Car Name</th><th>Car Brand</th></tr></thead><tbody>";
		for(Cars c:lc) {
			disp+="<tr><td>"+c.getCid()+"</td><td>"+c.getCname()+"</td><td>"+c.getCbrand()+"</td></tr>";
		}
		disp+="</tbody></table><center>";
		out.println("<center><h1>Welcome to car show room we have following cars for display</h1></center><br/><hr/><br/>");
		out.println(disp);
	}

	/**
	 * @see HttpServlet#doPost(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		doGet(request, response);
	}

}
/////
response.addHeader("content-type", "text/html");
/////
package co.cls.st;

import java.io.IOException;
import java.io.PrintWriter;
import java.util.List;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import co.cls.mods.Cars;
import co.cls.mods.ListCars;

/**
 * Servlet implementation class DetServe
 */
@WebServlet("/DetServe")
public class DetServe extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public DetServe() {
        super();
        // TODO Auto-generated constructor stub
    }

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		response.addHeader("content-type", "text/html");
		PrintWriter out=response.getWriter();
		out.println("Welcome to selection");
		List<Cars> lc=null;
		ListCars lcObj=new ListCars();
		lc=lcObj.retCList();
		String op="<form><select name=sel>";
		for(Cars c:lc) {
			op+="<option value="+c.getCid()+">"+c.getCid()+"</option>";
		}
		op+="</select><input type=submit value=Get /></form>";
		out.println(op);
		if(request.getParameter("sel")!=null) {
//			out.println("<br/>Selected Car Id is "+request.getParameter("sel"));
			String cont="<h2>";
			for(Cars c:lc) {
				if(c.getCid()==Integer.parseInt(request.getParameter("sel")))
				cont+="Name:"+c.getCname()+"<br/>Brand:"+c.getCbrand();
			}
			cont+="</h2>";
			out.println(cont);
		}
	}

	/**
	 * @see HttpServlet#doPost(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		doGet(request, response);
	}

}
/////////index.html//////
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Home page</title>
</head>
<body>
<table>
<tr><td><a href="./BServe">First Servlet</a></td>
<td><a href="./Index">Second Servlet</a></td>
<td><a href="./DetServe">Third Servlet</a></td></tr>
</table>
</body>
</html>
/////
package co.cls.st;

import java.io.IOException;
import java.io.PrintWriter;
import java.util.List;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import co.cls.mods.Cars;
import co.cls.mods.ListCars;

/**
 * Servlet implementation class DetServe
 */
@WebServlet("/DetServe")
public class DetServe extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public DetServe() {
        super();
        // TODO Auto-generated constructor stub
    }

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		response.addHeader("content-type", "text/html");
		PrintWriter out=response.getWriter();
		out.println("Welcome to selection");
		List<Cars> lc=null;
		ListCars lcObj=new ListCars();
		lc=lcObj.retCList();
		String op="<form><select name=sel>";
		for(Cars c:lc) {
			op+="<option value="+c.getCid()+">"+c.getCid()+"</option>";
		}
		op+="</select><input type=submit value=Get /></form>";
		out.println(op);
		if(request.getParameter("sel")!=null) {
//			out.println("<br/>Selected Car Id is "+request.getParameter("sel"));
			String cont="<br/><span>Details of the car selected</span><br/><h2>";
			for(Cars c:lc) {
				if(c.getCid()==Integer.parseInt(request.getParameter("sel")))
				cont+="Name:"+c.getCname()+"<br/>Brand:"+c.getCbrand();
			}
			cont+="</h2>";
			out.println(cont);
		}
	}

	/**
	 * @see HttpServlet#doPost(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		doGet(request, response);
	}

}
///////////
package co.cls.st;

import java.io.IOException;
import java.io.PrintWriter;
import java.util.List;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import co.cls.mods.Cars;
import co.cls.mods.ListCars;

/**
 * Servlet implementation class CarForm
 */
@WebServlet("/CarForm")
public class CarForm extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public CarForm() {
        super();
        // TODO Auto-generated constructor stub
    }

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		response.addHeader("content-type", "text/html");
		PrintWriter out=response.getWriter();
		ListCars lca=new ListCars();
		List<Cars> lc=lca.retCList();
		String op="<center><form><table><tr><td>Car Id</td><td><input type=text name=cid /></td></tr>";
		op+="<tr><td>Car Name</td><td><input type=text name=cname /></td></tr>";
		op+="<tr><td>Car Brand</td><td><input type=text name=cbrand /></td></tr>";
		op+="<tr><td><input type=submit value=Send /></td><td><input type=reset value=Cancel /></td></tr></table></form></center>";
		if(request.getParameter("cname")!=null) {
			int a=Integer.parseInt(request.getParameter("cid"));
			String b=request.getParameter("cname");
			String c=request.getParameter("cbrand");
			Cars cc=new Cars();
			cc.setCid(a);
			cc.setCname(b);
			cc.setCbrand(c);
			lc.add(cc);
			out.println("<ul>");
			for(Cars ca:lc) {
				out.println("<li>"+ca.getCid()+"&nbsp;"+ca.getCname()+"&nbsp;"+ca.getCbrand()+"</li>");
			}
			out.println("</ul>");
		}
	}

	/**
	 * @see HttpServlet#doPost(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		doGet(request, response);
	}

}
//////
package co.cls.st;

import java.io.IOException;
import java.io.PrintWriter;
import java.util.List;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import co.cls.mods.Cars;
import co.cls.mods.ListCars;

/**
 * Servlet implementation class CarForm
 */
@WebServlet("/CarForm")
public class CarForm extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public CarForm() {
        super();
        // TODO Auto-generated constructor stub
    }

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
    ListCars lca=new ListCars();
    List<Cars> lc=lca.retCList();
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		response.addHeader("content-type", "text/html");
		PrintWriter out=response.getWriter();
		String op="<center><h1>Car Entry Form</h1><br/><hr/><br/><form><table border=1><tr><td>Car Id</td><td><input type=text name=cid /></td></tr>";
		op+="<tr><td>Car Name</td><td><input type=text name=cname /></td></tr>";
		op+="<tr><td>Car Brand</td><td><input type=text name=cbrand /></td></tr>";
		op+="<tr><td><input type=submit value=Send /></td><td><input type=reset value=Cancel /></td></tr></table></form></center>";
		out.println(op+"<br/><hr/><br/>");
		if(request.getParameter("cname")!=null) {
			int a=Integer.parseInt(request.getParameter("cid"));
			String b=request.getParameter("cname");
			String c=request.getParameter("cbrand");
			Cars cc=new Cars();
			cc.setCid(a);
			cc.setCname(b);
			cc.setCbrand(c);
			lc.add(cc);
			out.println("<ul>");
			for(Cars ca:lc) {
				out.println("<li>"+ca.getCid()+"&nbsp;"+ca.getCname()+"&nbsp;"+ca.getCbrand()+"</li>");
			}
			out.println("</ul>");
		}
	}

	/**
	 * @see HttpServlet#doPost(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		doGet(request, response);
	}

}


/////
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Home page</title>
</head>
<body>
	<table>
		<tr>
			<td><a href="./BServe">First Servlet</a></td>
			<td><a href="./Index">Second Servlet</a></td>
			<td><a href="./DetServe">Third Servlet</a></td>
			<td><a href="./CarForm">Car Form</a></td>
		</tr>
	</table>
</body>
</html>
/////
response.addHeader("content-type", "text/html");
		PrintWriter out=response.getWriter();
		String j="Iam coming from previous servlet";
		HttpSession sess=request.getSession();
		Cars c=new Cars();
		c.setCid(212);
		c.setCname("Brando");
		c.setCbrand("Citroen");
		sess.setAttribute("val", j);
		sess.setAttribute("car", c);
		//Client Side
		Cookie cook=new Cookie("cooka", "This is val of cookie");
		response.addCookie(cook);
		//Client side
		response.sendRedirect("./SecServe?name=mukesh&email=mukesh@yahoo.com&mobile=93838383838");
		out.println("<h1>First Servlet</h1>");
////
	response.addHeader("content-type", "text/html");
		PrintWriter out=response.getWriter();
		HttpSession sess=request.getSession();
		if(sess.getAttribute("val")!=null) {
			out.println("<h1>The value from other serv is "+sess.getAttribute("val").toString()+"</h1>");
		}
		if(sess.getAttribute("car")!=null) {
			Cars cc=(Cars)sess.getAttribute("car");
			out.println(cc.getCid()+" "+cc.getCname()+" "+cc.getCbrand());
		}
		
		Cookie[] cArr=request.getCookies();
		for(Cookie co:cArr) {
			if(co.getName().equals("cooka"))
			out.println(co.getName()+" "+co.getValue());
		}
	
		String jj=request.getQueryString();
//		out.println("<br/>"+jj);
		String[] jArr=jj.split("&");
		for(String j:jArr) {
			String[] a=j.split("=");
			if(a.length>0)
			out.println(a[1]);
		}
/////
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Form A</title>
</head>
<body>
	<!--  -->

	<form action="http://localhost:8080/UnisysProjB/FormServA" method="post">
		<table>
			<tr>
				<td>Car Id</td>
				<td><input type="number" name="cid" /></td>
			</tr>
			<tr>
				<td>Car Name</td>
				<td><input type="text" name="cname" /></td>
			</tr>
			<tr>
				<td>Car Brand</td>
				<td><input type="text" name="cbrand" /></td>
			</tr>
			<tr>
				<td><input type="submit" value="Send" /></td>
				<td><input type="reset" value="Cancel" /></td>
			</tr>
		</table>
	</form>
</body>
</html>
/////
package co.cls.st;

import java.io.IOException;
import java.io.PrintWriter;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import co.cls.mods.Cars;

/**
 * Servlet implementation class FormServA
 */
@WebServlet("/FormServA")
public class FormServA extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public FormServA() {
        super();
        // TODO Auto-generated constructor stub
    }

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		PrintWriter out=response.getWriter();
		if(request.getParameter("cid")!=null) {
			int a=Integer.parseInt(request.getParameter("cid"));
			String b=request.getParameter("cname");
			String c=request.getParameter("cbrand");
			Cars cc=new Cars();
			cc.setCid(a);
			cc.setCname(b);
			cc.setCbrand(c);
			out.print(cc.getCid()+" "+cc.getCname()+" "+cc.getCbrand());
		}
	}

	/**
	 * @see HttpServlet#doPost(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
//		doGet(request, response);
		PrintWriter out=response.getWriter();
		if(request.getParameter("cid")!=null) {
			int a=Integer.parseInt(request.getParameter("cid"));
			String b=request.getParameter("cname");
			String c=request.getParameter("cbrand");
			Cars cc=new Cars();
			cc.setCid(a);
			cc.setCname(b);
			cc.setCbrand(c);
			out.print(cc.getCid()+" "+cc.getCname()+" "+cc.getCbrand());
		}
	
	
	}

}
///////
create database unifirst;
//////
create table cars(cid int primary key,cname varchar(50),cbrand varchar(50));
//////
desc cars;
////
insert into cars values(5,'Lexus','Nexus');
///////
//Start
			try {
				Class.forName("com.mysql.jdbc.Driver");
				Connection conn=DriverManager.getConnection("jdbc:mysql://localhost:3306/unifirst", "root", "admin");
				PreparedStatement ps=conn.prepareStatement("insert into cars values("+a+",'"+b+"','"+c+"')");
				ps.execute();
			} catch (ClassNotFoundException e) {
				e.printStackTrace();
			} catch (SQLException e) {
				e.printStackTrace();
			}


////////////////
package co.cls.st;

import java.io.IOException;
import java.io.PrintWriter;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.SQLException;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import co.cls.mods.Cars;

/**
 * Servlet implementation class FormServA
 */
@WebServlet("/FormServA")
public class FormServA extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public FormServA() {
        super();
        // TODO Auto-generated constructor stub
    }

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		PrintWriter out=response.getWriter();
		if(request.getParameter("cid")!=null) {
			int a=Integer.parseInt(request.getParameter("cid"));
			String b=request.getParameter("cname");
			String c=request.getParameter("cbrand");
			Cars cc=new Cars();
			cc.setCid(a);
			cc.setCname(b);
			cc.setCbrand(c);
			
			
			out.print(cc.getCid()+" "+cc.getCname()+" "+cc.getCbrand());
		}
	}

	/**
	 * @see HttpServlet#doPost(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
//		doGet(request, response);
		PrintWriter out=response.getWriter();
		if(request.getParameter("cid")!=null) {
			int a=Integer.parseInt(request.getParameter("cid"));
			String b=request.getParameter("cname");
			String c=request.getParameter("cbrand");
			Cars cc=new Cars();
			cc.setCid(a);
			cc.setCname(b);
			cc.setCbrand(c);
			
			//Start
			try {
				Class.forName("com.mysql.jdbc.Driver");
				Connection conn=DriverManager.getConnection("jdbc:mysql://localhost:3306/unifirst", "root", "admin");
				PreparedStatement ps=conn.prepareStatement("insert into cars values("+a+",'"+b+"','"+c+"')");
				ps.execute();
				out.println("Data Inserted<br/>");
			} catch (ClassNotFoundException e) {
				e.printStackTrace();
			} catch (SQLException e) {
				e.printStackTrace();
			}
			
			//End
			
			out.print(cc.getCid()+" "+cc.getCname()+" "+cc.getCbrand());
		}
	
	
	}

}
///////////
package co.cls.st;

import java.io.IOException;
import java.io.PrintWriter;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.SQLException;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import co.cls.mods.Cars;

/**
 * Servlet implementation class FormServA
 */
@WebServlet("/FormServA")
public class FormServA extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public FormServA() {
        super();
        // TODO Auto-generated constructor stub
    }

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		PrintWriter out=response.getWriter();
		if(request.getParameter("cid")!=null) {
			int a=Integer.parseInt(request.getParameter("cid"));
			String b=request.getParameter("cname");
			String c=request.getParameter("cbrand");
			Cars cc=new Cars();
			cc.setCid(a);
			cc.setCname(b);
			cc.setCbrand(c);
			
			
			out.print(cc.getCid()+" "+cc.getCname()+" "+cc.getCbrand());
		}
	}

	/**
	 * @see HttpServlet#doPost(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
//		doGet(request, response);
		PrintWriter out=response.getWriter();
		if(request.getParameter("cid")!=null) {
			int a=Integer.parseInt(request.getParameter("cid"));
			String b=request.getParameter("cname");
			String c=request.getParameter("cbrand");
			Cars cc=new Cars();
			cc.setCid(a);
			cc.setCname(b);
			cc.setCbrand(c);
			
			//Start
			try {
				Class.forName("com.mysql.jdbc.Driver");
				Connection conn=DriverManager.getConnection("jdbc:mysql://localhost:3306/unifirst", "root", "admin");
				PreparedStatement ps=conn.prepareStatement("insert into cars values("+a+",'"+b+"','"+c+"')");
				ps.execute();
//				out.println("Data Inserted<br/>");
			} catch (ClassNotFoundException e) {
				e.printStackTrace();
			} catch (SQLException e) {
				e.printStackTrace();
			}
			
			//End
			
//			out.print(cc.getCid()+" "+cc.getCname()+" "+cc.getCbrand());
			response.sendRedirect("./FormA.html");
		}
	
	
	}

}
///////
package co.cls.st;

import java.io.IOException;
import java.io.PrintWriter;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

/**
 * Servlet implementation class SelServe
 */
@WebServlet("/SelServe")
public class SelServe extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public SelServe() {
        super();
        // TODO Auto-generated constructor stub
    }

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		PrintWriter out=response.getWriter();
		response.setContentType("text/html");
		out.println("<h1>List Of Cars In Our Garaga</h1><br/><hr/><br/>");
		//Start
		try {
			Class.forName("com.mysql.jdbc.Driver");
			Connection conn=DriverManager.getConnection("jdbc:mysql://localhost:3306/unifirst", "root", "admin");
			Statement st=conn.createStatement();
			ResultSet rs=st.executeQuery("select * from cars");
			out.println("<center><table border=1><tr><td>CarID</td><td>Car Name</td><td>Car Brand</tr>");
			while(rs.next()) {
				out.println("<tr><td>"+rs.getInt(1)+"</td><td>"+rs.getString(2)+"</td><td>"+rs.getString(3)+"</td></tr>");
			}
			out.println("</table></center>");
		} catch (ClassNotFoundException e) {
			e.printStackTrace();
		} catch (SQLException e) {
			e.printStackTrace();
		}
		//End
	}

	/**
	 * @see HttpServlet#doPost(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		doGet(request, response);
	}

}
////
PreparedStatement ps=conn.prepareStatement("update cars set cname='"+b+"',cbrand='"+c+"' where cid="+a);
				ps.executeUpdate();

/////
PreparedStatement ps=conn.prepareStatement("delete from cars where cid="+a);
				ps.executeUpdate();
/////
DELIMITER $$
CREATE DEFINER=`root`@`localhost` PROCEDURE `spcars`()
BEGIN
select * from cars;
END$$
DELIMITER ;
package co.tis.p1;
import java.io.IOException;
import java.io.PrintWriter;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.SQLException;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import co.tis.p2.Cars;

/**
 * Servlet implementation class FormServA
 */
@WebServlet("/FormServA")
public class FormServA extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public FormServA() {
        super();
        // TODO Auto-generated constructor stub
    }

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		PrintWriter out=response.getWriter();
		if(request.getParameter("cid")!=null) {
			int a=Integer.parseInt(request.getParameter("cid"));
			String b=request.getParameter("cname");
			String c=request.getParameter("cbrand");
			Cars cc=new Cars();
			cc.setCid(a);
			cc.setCname(b);
			cc.setCbrand(c);
			out.print(cc.getCid()+" "+cc.getCname()+" "+cc.getCbrand());
			
		}
	}

	/**
	 * @see HttpServlet#doPost(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
//		doGet(request, response);
		PrintWriter out=response.getWriter();
		if(request.getParameter("cid")!=null) {
			int a=Integer.parseInt(request.getParameter("cid"));
			String b=request.getParameter("cname");
			String c=request.getParameter("cbrand");
			Cars cc=new Cars();
			cc.setCid(a);
			cc.setCname(b);
			cc.setCbrand(c);
			//Start
			try {
				Class.forName("com.mysql.jdbc.Driver");
				Connection conn=DriverManager.getConnection("jdbc:mysql://localhost:3306/unifirst", "root", "unisys@1321");
				PreparedStatement ps=conn.prepareStatement("insert into cars values("+a+",'"+b+"','"+c+"')");
				//PreparedStatement ps=conn.prepareStatement("update cars set cname='"+b+"',cbrand='"+c+"' where cid="+a);
				//ps.executeUpdate();
				ps.execute();
				out.println("Data Inserted<br/>");
			} catch (ClassNotFoundException e) {
				e.printStackTrace();
			} catch (SQLException e) {
				e.printStackTrace();
			}
			
			//End
			
			out.print(cc.getCid()+" "+cc.getCname()+" "+cc.getCbrand());
		}
	
	
	}

}

======
package co.tis.p1;
import java.io.IOException;
import java.io.PrintWriter;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.SQLException;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import co.tis.p2.Cars;

/**
 * Servlet implementation class FormServA
 */
@WebServlet("/FormServA")
public class FormServA extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public FormServA() {
        super();
        // TODO Auto-generated constructor stub
    }

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		PrintWriter out=response.getWriter();
		if(request.getParameter("cid")!=null) {
			int a=Integer.parseInt(request.getParameter("cid"));
			String b=request.getParameter("cname");
			String c=request.getParameter("cbrand");
			Cars cc=new Cars();
			cc.setCid(a);
			cc.setCname(b);
			cc.setCbrand(c);
			out.print(cc.getCid()+" "+cc.getCname()+" "+cc.getCbrand());
			
		}
	}

	/**
	 * @see HttpServlet#doPost(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
//		doGet(request, response);
		PrintWriter out=response.getWriter();
		if(request.getParameter("cid")!=null) {
			int a=Integer.parseInt(request.getParameter("cid"));
			String b=request.getParameter("cname");
			String c=request.getParameter("cbrand");
			Cars cc=new Cars();
			cc.setCid(a);
			cc.setCname(b);
			cc.setCbrand(c);
			//Start
			try {
				Class.forName("com.mysql.jdbc.Driver");
				Connection conn=DriverManager.getConnection("jdbc:mysql://localhost:3306/unifirst", "root", "unisys@1321");
				PreparedStatement ps=conn.prepareStatement("insert into cars values("+a+",'"+b+"','"+c+"')");
				//PreparedStatement ps=conn.prepareStatement("update cars set cname='"+b+"',cbrand='"+c+"' where cid="+a);
				//ps.executeUpdate();
				ps.execute();
				out.println("Data Inserted<br/>");
			} catch (ClassNotFoundException e) {
				e.printStackTrace();
			} catch (SQLException e) {
				e.printStackTrace();
			}
			
			//End
			
			out.print(cc.getCid()+" "+cc.getCname()+" "+cc.getCbrand());
		}
	
	
	}

}

=================
package co.tis.p1;

import java.io.IOException;
import java.io.PrintWriter;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

/**
 * Servlet implementation class SelServe
 */
@WebServlet("/SelServe")
public class SelServe extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public SelServe() {
        super();
        // TODO Auto-generated constructor stub
    }

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		PrintWriter out=response.getWriter();
		response.setContentType("text/html");
		out.println("<h1>List Of Cars In Our Garaga</h1><br/><hr/><br/>");
		//Start
		try {
			Class.forName("com.mysql.jdbc.Driver");
			Connection conn=DriverManager.getConnection("jdbc:mysql://localhost:3306/unifirst", "root", "unisys@1321");
			Statement st=conn.createStatement();
			ResultSet rs=st.executeQuery("select * from cars");
			out.println("<center><table border=1><tr><td>CarID</td><td>Car Name</td><td>Car Brand</tr>");
			while(rs.next()) {
				out.println("<tr><td>"+rs.getInt(1)+"</td><td>"+rs.getString(2)+"</td><td>"+rs.getString(3)+"</td></tr>");
			}
			out.println("</table></center>");
		} catch (ClassNotFoundException e) {
			e.printStackTrace();
		} catch (SQLException e) {
			e.printStackTrace();
		}
		
	}

	/**
	 * @see HttpServlet#doPost(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		doGet(request, response);
	}

}
/////////////14-05-2024///////////
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
	pageEncoding="ISO-8859-1"%>
c
////
[disconnected /] connect
The controller is not available at localhost:9999
[disconnected /]
/////////////
package co.sa.cl;

public class Books {
	public int getBid() {
		return bid;
	}
	public void setBid(int bid) {
		this.bid = bid;
	}
	public String getBanme() {
		return banme;
	}
	public void setBanme(String banme) {
		this.banme = banme;
	}
	public String getBauth() {
		return bauth;
	}
	public void setBauth(String bauth) {
		this.bauth = bauth;
	}
	private int bid;
	private String banme;
	private String bauth;
}
/////
<%@page import="co.sa.cl.BookList"%>
<%@page import="java.util.List"%>
<%@page import="co.sa.cl.Books"%>
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
	pageEncoding="ISO-8859-1"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Test</title>
</head>
<%!String[] arr = { "Physics", "nuclear Physics", "Geo Physics", "Nano Physics", "Meta Physics" };%>
<body>

	<%
	out.println("<h1>This is JSP Welcome!</h1>");
	%>
	<ul
		style="background-color: gray; color: maroon; list-style-type: hebrew;">
		<%
		for (String j : arr) {
		%>
		<li><%=j.toUpperCase()%></li>
		<%
		}
		%>
	</ul>
	<br />
	<%
	Books b = new Books();
	b.setBid(212);
	b.setBanme("Last Sigh Of Moor");
	b.setBauth("Salman Rushdie");
	List<Books> lb = null;
	BookList blist = new BookList();
	lb = blist.retList();
	%>
	<table>
		<tr>
			<td><%=b.getBid()%></td>
			<td><%=b.getBanme()%></td>
			<td><%=b.getBauth()%></td>
		</tr>
	</table>
	<br />
	<hr />
	<br />
	<h1>List Of Books</h1>
	<br />
	<table border=1 style="background-color: navy;color:yellow;">
		<thead>
			<tr>
				<th>Book ID</th>
				<th>Book Name</th>
				<th>Book Author</th>
			</tr>
		</thead>
		<tbody>
			<%
			for (Books book : lb) {
			%>
			<tr>
				<td><%=book.getBid()%></td>
				<td><%=book.getBanme()%></td>
				<td><%=book.getBauth()%></td>
			</tr>
			<%
			}
			%>
		</tbody>
	</table>
</body>
</html>
/////
package co.sa.cl;


import java.util.ArrayList;
import java.util.List;

public class BookList {
	public List<Books> retList(){
		List<Books> ls=new ArrayList<Books>();
		int[] arr1= {1,2,3,4,5};
		String[] arr2= {"Adventures of tom sawyer","Kane and abel","elephant song","Pelican brief","God of small things"};
		String[] arr3= {"Mark twain","J Archer","Wilbur smith","John Grisham","Arundhati roy"};
		for (int i = 0; i < arr3.length; i++) {
			Books b=new Books();
			b.setBid(arr1[i]);
			b.setBanme(arr2[i]);
			b.setBauth(arr3[i]);
			ls.add(b);
		}
		return ls;
	}
}
//////
/////
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Insert title here</title>
</head>
<body>
<form method="get" action="http://localhost:8080/UnisysProjC/bpage.jsp">
		<table>
			<tr>
				<td>Book Id</td>
				<td><input type="number" required="required"
					placeholder="enter id" name="bid" /></td>
			</tr>
			<tr>
				<td>Book Name</td>
				<td><input type="text" required="required"
					placeholder="enter name" name="bname" /></td>
			</tr>
			<tr>
				<td>Book Author</td>
				<td><input type="text" required="required"
					placeholder="enter author" name="bauth" /></td>
			</tr>
			<tr>
				<td><input type="submit" value="Submit" /></td>
				<td><input type="reset" value="cancel" /></td>
			</tr>
		</table>
	</form>
</body>
</html>
////
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Target</title>
</head>
<body>
<%
String j=request.getQueryString();
//out.println(j);
String arr[]=j.split("&");
for(String a:arr){
	String h[]=a.split("=");
	if(h.length>0){
		out.println(h[1]+"<br/>");
	}
}

%>
</body>
</html>
/////////////
<%@page import="co.sa.cl.Books"%>
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Insert title here</title>
</head>
<body>
<form method="post">
		<table>
			<tr>
				<td>Book Id</td>
				<td><input type="number" required="required"
					placeholder="enter id" name="bid" /></td>
			</tr>
			<tr>
				<td>Book Name</td>
				<td><input type="text" required="required"
					placeholder="enter name" name="bname" /></td>
			</tr>
			<tr>
				<td>Book Author</td>
				<td><input type="text" required="required"
					placeholder="enter author" name="bauth" /></td>
			</tr>
			<tr>
				<td><input type="submit" value="Submit" /></td>
				<td><input type="reset" value="cancel" /></td>
			</tr>
		</table>
	</form>
	<%
	if(request.getParameter("bid")!=null){
		int a=Integer.parseInt(request.getParameter("bid"));
		String b=request.getParameter("bname");
		String c=request.getParameter("bauth");
		Books ba=new Books();
		ba.setBid(a);
		ba.setBanme(b);
		ba.setBauth(c);
		session.setAttribute("book", ba);
		Cookie cook=new Cookie("cook",ba.getBanme()+" "+ba.getBauth());
		response.addCookie(cook);
		out.println("<form action=\"http://localhost:8080/UnisysProjC/dpage.jsp\"><input type=submit value=Send /></form>");
	}
	%>
</body>
</html>
//////
<%@page import="co.sa.cl.Books"%>
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Target</title>
</head>
<body>
<%
Books ba=(Books)session.getAttribute("book");
out.println(ba.getBid()+" "+ba.getBanme()+" "+ba.getBauth());
Cookie[] cArr=request.getCookies();
for(Cookie c:cArr){
	if(c.getName().equals("cook"))
	out.println("<br/><hr/><br/>"+c.getValue()); 
}
%>
</body>
</html>
/////
package com.sat.mods;


public class Register {
	public int getId() {
		return id;
	}
	public void setId(int id) {
		this.id = id;
	}
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	public String getEmail() {
		return email;
	}
	public void setEmail(String email) {
		this.email = email;
	}
	public String getMobile() {
		return mobile;
	}
	public void setMobile(String mobile) {
		this.mobile = mobile;
	}
	private int id;
	private String name;
	private String email;
	private String mobile;
}

////
package com.sa.db;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.util.ArrayList;
import java.util.List;

import com.sat.mods.Register;

public class DbUtils {
	Connection conn = null;

	public DbUtils() {
		try {
			Class.forName("com.mysql.jdbc.Driver");
			conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/unifirst", "root", "admin");
		} catch (ClassNotFoundException e) {
			e.printStackTrace();
		} catch (SQLException e) {
			e.printStackTrace();
		}
	}

	public List<Register> retRegs() {
		List<Register> lreg=new ArrayList<Register>();
		try {
			PreparedStatement ps=conn.prepareStatement("select * from register");
			ResultSet rs=ps.executeQuery();
			while(rs.next()) {
				Register r=new Register();
				r.setId(rs.getInt(1));
				r.setName(rs.getString(2));
				r.setEmail(rs.getString(3));
				r.setMobile(rs.getString(4));
				lreg.add(r);
			}
		} catch (SQLException e) {
			e.printStackTrace();
		}
		return lreg;
	}

	public String insReg(Register r) {

		return "";
	}

	public String upsReg(Register r) {
		return "";
	}

	public String delReg(int id) {
		return "";
	}

}
/////
package com.sa.db;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.util.ArrayList;
import java.util.List;
import com.sat.mods.Register;

public class DbUtils {
	Connection conn = null;

	public DbUtils() {
		try {
			Class.forName("com.mysql.jdbc.Driver");
			conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/unifirst", "root", "admin");
		} catch (ClassNotFoundException e) {
			e.printStackTrace();
		} catch (SQLException e) {
			e.printStackTrace();
		}
	}

	/***
	 * Select query on table
	 * @return List of register objects from db
	 */
	public List<Register> retRegs() {
		List<Register> lreg=new ArrayList<Register>();
		try {
			PreparedStatement ps=conn.prepareStatement("select * from register");
			ResultSet rs=ps.executeQuery();
			while(rs.next()) {
				Register r=new Register();
				r.setId(rs.getInt(1));
				r.setName(rs.getString(2));
				r.setEmail(rs.getString(3));
				r.setMobile(rs.getString(4));
				lreg.add(r);
			}
		} catch (SQLException e) {
			e.printStackTrace();
		}
		return lreg;
	}

	/***
	 * Inserts a new record into the table
	 * @param r
	 * @return
	 */
	public String insReg(Register r) {
		String status="Notdone";
		int a=r.getId();
		String b=r.getName();
		String c=r.getEmail();
		String d=r.getMobile();
		String query="insert into register values (?,?,?,?)";
		try {
			PreparedStatement ps=conn.prepareStatement(query);
			ps.setInt(1, a);
			ps.setString(2, b);
			ps.setString(3, c);
			ps.setString(4, d);
			ps.execute();
			status="done";
		} catch (SQLException e) {
			e.printStackTrace();
		}
		return status;
	}

	/***
	 * Updates the given record into the table
	 * @param r
	 * @return
	 */
	public String upsReg(Register r) {
		String status="Notdone";
		int a=r.getId();
		String b=r.getName();
		String c=r.getEmail();
		String d=r.getMobile();
		String query="update register set name=?,email=?,mobile=? where id=?";
		try {
			PreparedStatement ps=conn.prepareStatement(query);
			ps.setString(1, b);
			ps.setString(2, c);
			ps.setString(3, d);
			ps.setInt(4, a);
			ps.executeUpdate();
			status="done";
		} catch (SQLException e) {
			e.printStackTrace();
		}
		return status;
	}

	/***
	 * Deletes the record from the register table
	 * @param id
	 * @return
	 */
	public String delReg(int id) {
		String status="Notdone";
		String query="delete from register where id=?";
		try {
			PreparedStatement ps=conn.prepareStatement(query);
			ps.setInt(1, id);
			ps.executeUpdate();
			status="done";
		} catch (SQLException e) {
			e.printStackTrace();
		}
		return status;
	}
}
//////index.jsp////
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Landing page</title>
</head>
<body>
<%@include file="./menu.jsp" %>
<h1>Portal pages for crud ops on Register table</h1>

</body>
</html>
////menu.jsp/////
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
	pageEncoding="ISO-8859-1"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
</head>
<body>
	<table>
		<tr>
			<td><a href="./selpage.jsp">Select</a></td>
			<td><a href="./inspage.jsp">Insert</a></td>
			<td><a href="./upspage.jsp">Update</a></td>
			<td><a href="./delpage.jsp">Delete</a></td>
		</tr>
	</table>
</body>
</html>
///////selepage.jsp/////
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Select</title>
</head>
<body>
<%@include file="./menu.jsp" %>
<h1>Selection of all records on register table</h1>
</body>
</html>
////////inspage.jsp/////
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Insert</title>
</head>
<body>
<%@include file="./menu.jsp" %>
<h1>Insert a new record into the table</h1>
</body>
</html>
///////upspage.jsp///////
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Update</title>
</head>
<body>
<%@include file="./menu.jsp" %>
<h1>Update an old record in the table</h1>
</body>
</html>
//////delpage.jsp/////
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Delete</title>
</head>
<body>
<%@include file="./menu.jsp" %>
<h1>Delete a record from the table</h1>
</body>
</html>
/////
<%@page import="com.sat.mods.Register"%>
<%@page import="java.util.List"%>
<%@page import="com.sa.db.DbUtils"%>
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
	pageEncoding="ISO-8859-1"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Select</title>
</head>
<%!DbUtils du = new DbUtils();
	List<Register> lr = du.retRegs();%>
<body>
	<%@include file="./menu.jsp"%>
	<h1>Selection of all records on register table</h1>
	<center>
		<table>
			<thead>
				<tr>
					<th>ID</th>
					<th>Name</th>
					<th>Email</th>
					<th>Mobile</th>
				</tr>
			</thead>
			<tbody>
				<%
				for (Register r : lr) {
					out.println("<tr><td>" + r.getId() + "</td><td>" + r.getName() + "</td><td>" + r.getEmail() + "</td><td>"
					+ r.getMobile() + "</td></tr>");
				}
				%>
			</tbody>
		</table>
	</center>
</body>
</html>
/////selpage.jsp/////
<%@page import="com.sat.mods.Register"%>
<%@page import="java.util.List"%>
<%@page import="com.sa.db.DbUtils"%>
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
	pageEncoding="ISO-8859-1"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Select</title>
</head>
<%!DbUtils du = new DbUtils();
	List<Register> lr = du.retRegs();%>
<body>
	<%@include file="./menu.jsp"%>
	<h1>Selection of all records on register table</h1>
	<center>
		<table>
			<thead>
				<tr>
					<th>ID</th>
					<th>Name</th>
					<th>Email</th>
					<th>Mobile</th>
				</tr>
			</thead>
			<tbody>
				<%
				for (Register r : lr) {
					out.println("<tr><td>" + r.getId() + "</td><td>" + r.getName() + "</td><td>" + r.getEmail() + "</td><td>"
					+ r.getMobile() + "</td></tr>");
				}
				%>
			</tbody>
		</table>
	</center>
</body>
</html>
//////inspage.jsp////
<%@page import="com.sat.mods.Register"%>
<%@page import="com.sa.db.DbUtils"%>
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Insert</title>
</head>
<%!DbUtils du=new DbUtils(); %>
<body>
<%@include file="./menu.jsp" %>
<h1>Insert a new record into the table</h1>
<form>
<table>
<tr><td>Id</td><td><input type="text" name="id" placeholder="Enter Id" /></td></tr>
<tr><td>Name</td><td><input type="text" name="name" placeholder="Enter name" /></td></tr>
<tr><td>Email</td><td><input type="text" name="email" placeholder="Enter Email" /></td></tr>
<tr><td>Mobile</td><td><input type="text" name="mobile" placeholder="Enter mobile" /></td></tr>
<tr><td><input type="submit" value="Send" /></td><td><input type="reset" value="Cancel" /></td></tr>
</table>
</form>
<%
if(request.getParameter("id")!=null){
	int a=Integer.parseInt(request.getParameter("id"));
	String b=request.getParameter("name");
	String c=request.getParameter("email");
	String d=request.getParameter("mobile");
	Register r=new Register();
	r.setId(a);
	r.setName(b);
	r.setEmail(c);
	r.setMobile(d);
	du.insReg(r);
	response.sendRedirect("./selpage.jsp");
}

%>

</body>
</html>
////upspage.jsp/////
<%@page import="com.sa.db.DbUtils"%>
<%@page import="com.sat.mods.Register"%>
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Update</title>
</head>
<%!DbUtils du=new DbUtils(); %>
<body>
<%@include file="./menu.jsp" %>
<h1>Update an old record in the table</h1>
<form>
<table>
<tr><td>Id</td><td><input type="text" name="id" placeholder="Enter Id" /></td></tr>
<tr><td>Name</td><td><input type="text" name="name" placeholder="Enter name" /></td></tr>
<tr><td>Email</td><td><input type="text" name="email" placeholder="Enter Email" /></td></tr>
<tr><td>Mobile</td><td><input type="text" name="mobile" placeholder="Enter mobile" /></td></tr>
<tr><td><input type="submit" value="Send" /></td><td><input type="reset" value="Cancel" /></td></tr>
</table>
</form>
<%
if(request.getParameter("id")!=null){
	int a=Integer.parseInt(request.getParameter("id"));
	String b=request.getParameter("name");
	String c=request.getParameter("email");
	String d=request.getParameter("mobile");
	Register r=new Register();
	r.setId(a);
	r.setName(b);
	r.setEmail(c);
	r.setMobile(d);
	du.upsReg(r);
	response.sendRedirect("./selpage.jsp");
}

%>

</body>
</html>
/////delpage.jsp//////
<%@page import="com.sat.mods.Register"%>
<%@page import="com.sa.db.DbUtils"%>
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Delete</title>
</head>
<%!DbUtils du=new DbUtils(); %>
<body>
<%@include file="./menu.jsp" %>
<h1>Delete a record from the table</h1>
<form>
<table>
<tr><td>Id</td><td><input type="text" name="id" placeholder="Enter Id" /></td></tr>
<tr><td><input type="submit" value="Send" /></td><td><input type="reset" value="Cancel" /></td></tr>
</table>
</form>
<%
if(request.getParameter("id")!=null){
	int a=Integer.parseInt(request.getParameter("id"));
	du.delReg(a);
	response.sendRedirect("./selpage.jsp");
}
%>
</body>
</html>
/////



public List<Register> retRegs() {
		List<Register> lreg=new ArrayList<Register>();
		try {
			PreparedStatement ps=conn.prepareStatement("select * from register");
			ResultSet rs=ps.executeQuery();
			while(rs.next()) {
				Register r=new Register();
				r.setId(rs.getInt(1));
				r.setName(rs.getString(2));
				r.setEmail(rs.getString(3));
				r.setMobile(rs.getString(4));
				lreg.add(r);
			}
		} catch (SQLException e) {
			e.printStackTrace();
		}
		return lreg;
	}


////
package com.sa.db;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.util.ArrayList;
import java.util.List;
import com.sat.mods.Register;

public class DbUtils {
	Connection conn = null;

	public DbUtils() {
		try {
			Class.forName("com.mysql.jdbc.Driver");
			conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/unifirst", "root", "admin");
		} catch (ClassNotFoundException e) {
			e.printStackTrace();
		} catch (SQLException e) {
			e.printStackTrace();
		}
	}

	/***
	 * Select query on table
	 * @return List of register objects from db
	 */
	public List<Register> retRegs() {
		List<Register> lreg=new ArrayList<Register>();
		try {
			PreparedStatement ps=conn.prepareStatement("select * from register");
			ResultSet rs=ps.executeQuery();
			while(rs.next()) {
				Register r=new Register();
				r.setId(rs.getInt(1));
				r.setName(rs.getString(2));
				r.setEmail(rs.getString(3));
				r.setMobile(rs.getString(4));
				lreg.add(r);
			}
		} catch (SQLException e) {
			e.printStackTrace();
		}
		return lreg;
	}

	/***
	 * Inserts a new record into the table
	 * @param r
	 * @return
	 */
	public String insReg(Register r) {
		String status="Notdone";
		int a=r.getId();
		String b=r.getName();
		String c=r.getEmail();
		String d=r.getMobile();
		String query="insert into register values (?,?,?,?)";
		try {
			PreparedStatement ps=conn.prepareStatement(query);
			ps.setInt(1, a);
			ps.setString(2, b);
			ps.setString(3, c);
			ps.setString(4, d);
			ps.execute();
			status="done";
		} catch (SQLException e) {
			e.printStackTrace();
		}
		return status;
	}

	/***
	 * Updates the given record into the table
	 * @param r
	 * @return
	 */
	public String upsReg(Register r) {
		String status="Notdone";
		int a=r.getId();
		String b=r.getName();
		String c=r.getEmail();
		String d=r.getMobile();
		String query="update register set name=?,email=?,mobile=? where id=?";
		try {
			PreparedStatement ps=conn.prepareStatement(query);
			ps.setString(1, b);
			ps.setString(2, c);
			ps.setString(3, d);
			ps.setInt(4, a);
			ps.executeUpdate();
			status="done";
		} catch (SQLException e) {
			e.printStackTrace();
		}
		return status;
	}

	/***
	 * Deletes the record from the register table
	 * @param id
	 * @return
	 */
	public String delReg(int id) {
		String status="Notdone";
		String query="delete from register where id=?";
		try {
			PreparedStatement ps=conn.prepareStatement(query);
			ps.setInt(1, id);
			ps.executeUpdate();
			status="done";
		} catch (SQLException e) {
			e.printStackTrace();
		}
		return status;
	}
}
/////
<%@include file="./menu.jsp"%>
	<h1>Selection of all records on register table</h1>
	<center>
		<table>
			<thead>
				<tr>
					<th>ID</th>
					<th>Name</th>
					<th>Email</th>
					<th>Mobile</th>
				</tr>
			</thead>
			<tbody>
				<%
				for (Register r : lr) {
					out.println("<tr><td>" + r.getId() + "</td><td>" + r.getName() + "</td><td>" + r.getEmail() + "</td><td>"
					+ r.getMobile() + "</td></tr>");
				}
				%>
			</tbody>
		</table>
	</center>

//////
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Insert title here</title>
</head>
<body>
<%
session.setAttribute("tester", "Gargoyle gangs of JSP");
out.println("<form action=\"http://localhost:8080/UnisysProjC/FirstServe\"><input type=submit value=Send /></form> ");
%>
</body>
</html>
/////
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
    pageEncoding="ISO-8859-1"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="ISO-8859-1">
<title>Insert title here</title>
</head>
<body>
<h1>This is op page</h1>
<%
String j=session.getAttribute("atest").toString();
out.println("<h1>"+j+"</h1>");
%>
</body>
</html>
/////
package com.sa.serv;

import java.io.IOException;
import java.io.PrintWriter;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import javax.servlet.http.HttpSession;

/**
 * Servlet implementation class FirstServe
 */
@WebServlet("/FirstServe")
public class FirstServe extends HttpServlet {
	private static final long serialVersionUID = 1L;
       
    /**
     * @see HttpServlet#HttpServlet()
     */
    public FirstServe() {
        super();
        // TODO Auto-generated constructor stub
    }

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		PrintWriter out=response.getWriter();
		HttpSession sess=request.getSession();
		String u=sess.getAttribute("tester").toString();
		out.println("<h1>"+u+"</h1>");
		sess.setAttribute("atest", "EJB was ruling the world before spring");
		response.sendRedirect("http://localhost:8080/UnisysProjC/oppage.jsp");
	}

	/**
	 * @see HttpServlet#doPost(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		doGet(request, response);
	}

}
/////

//////
EJb is a distributed transactional enterprise app framework which runs on top app server(JBoss, Weblogic....)

EJB offers 3 types of beans:
Session
-stateful
-stateless
Entity(Persistence):
Send data to db
Message Driven Bean: Artemis MQ(Message Queue)(Stateless)
Timer Service:(Stateless)
Is to perform a certain task at fixed interval of time
/////////
https://www.transfernow.net/dl/20240515oM1FrNkf/8ihcgeM9
/////Server Code////
package com.ejb.ser.sat;

import javax.ejb.Remote;

@Remote
public interface FirstBeanRemote {
	public String myMetha();
}
////
package com.ejb.ser.sat;

import javax.ejb.Stateless;


@Stateless
public class FirstBean implements FirstBeanRemote {
    public FirstBean() {
    }

	@Override
	public String myMetha() {
		return "Welcome to EJB";
	}
}

/////Client Code/////
package com.sat.ejb.clienta;

import java.util.Properties;

import javax.naming.Context;
import javax.naming.InitialContext;
import javax.naming.NamingException;

import com.ejb.ser.sat.FirstBean;
import com.ejb.ser.sat.FirstBeanRemote;

public class FirstClient {
	public static void main(String[] args) throws NamingException {
		FirstBeanRemote fb=EJBContextFactory.retBean("ejb:");
		System.out.println("********"+fb.myMetha());
	}
	
	private static class EJBContextFactory{
		
		private static FirstBeanRemote retBean(String namespace) throws NamingException {
			return retLookUp(namespace);
		}
		
		private static FirstBeanRemote retLookUp(String namespace) throws NamingException {
			Context ctx=creaInitContext();
			String appName="";
			String moduleName="UnisysFirstProj";
			String distinctName="";
			String beanName=FirstBean.class.getSimpleName();
			String ViewClassName=FirstBeanRemote.class.getName();
			return (FirstBeanRemote)ctx.lookup(namespace+appName+"/"+moduleName+"/"+distinctName+"/"+beanName+"!"+ViewClassName);
		}
		
		private static Context creaInitContext() throws NamingException {
			Properties props=new Properties();
			props.put(Context.INITIAL_CONTEXT_FACTORY, "org.jboss.naming.remote.client.InitialContextFactory");
			props.put(Context.URL_PKG_PREFIXES, "org.jboss.ejb.client.naming");
			props.put(Context.PROVIDER_URL, "http-remoting://localhost:8080");
			props.put("jboss.naming.client.ejb.context", true);
			return new InitialContext(props);
		}
	}

}
////
    jndiProperties.put(Context.SECURITY_PRINCIPAL, "admin");
		jndiProperties.put(Context.SECURITY_CREDENTIALS, "Satish@123");
/////
guest=guest
jmsuser=guest
satish=Application,guest
May 15, 2024 5:15:47 AM org.jboss.naming.remote.client.InitialContextFactory <clinit>
INFO: WFNAM00025: org.jboss.naming.remote.client.InitialContextFactory is deprecated; new applications should use org.wildfly.naming.client.WildFlyInitialContextFactory instead
May 15, 2024 5:15:47 AM org.wildfly.naming.client.Version <clinit>
INFO: WildFly Naming version 1.0.7.Final-redhat-1
Exception in thread "main" java.lang.ExceptionInInitializerError
	at org.wildfly.security.auth.client.AuthenticationConfiguration.<clinit>(AuthenticationConfiguration.java:166)
	at org.wildfly.naming.client.ProviderEnvironment$Builder.populateFromEnvironment(ProviderEnvironment.java:329)
	at org.wildfly.naming.client.WildFlyRootContext.<init>(WildFlyRootContext.java:114)
	at org.wildfly.naming.client.WildFlyRootContext.<init>(WildFlyRootContext.java:89)
	at org.wildfly.naming.client.WildFlyRootContext.<init>(WildFlyRootContext.java:79)
	at org.wildfly.naming.client.WildFlyInitialContextFactory.getInitialContext(WildFlyInitialContextFactory.java:54)
	at org.jboss.naming.remote.client.InitialContextFactory.getInitialContext(InitialContextFactory.java:64)
	at java.naming/javax.naming.spi.NamingManager.getInitialContext(NamingManager.java:732)
	at java.naming/javax.naming.InitialContext.getDefaultInitCtx(InitialContext.java:305)
	at java.naming/javax.naming.InitialContext.init(InitialContext.java:236)
	at java.naming/javax.naming.InitialContext.<init>(InitialContext.java:208)
	at com.sat.ejb.clienta.FirstClient$EJBContextFactory.creaInitContext(FirstClient.java:44)
	at com.sat.ejb.clienta.FirstClient$EJBContextFactory.retLookUp(FirstClient.java:27)
	at com.sat.ejb.clienta.FirstClient$EJBContextFactory.retBean(FirstClient.java:23)
	at com.sat.ejb.clienta.FirstClient$EJBContextFactory.access$0(FirstClient.java:22)
	at com.sat.ejb.clienta.FirstClient.main(FirstClient.java:15)
Caused by: java.lang.reflect.InaccessibleObjectException: Unable to make field private java.security.ProtectionDomain[] java.security.AccessControlContext.context accessible: module java.base does not "opens java.security" to unnamed module @1efee8e7
	at java.base/java.lang.reflect.AccessibleObject.checkCanSetAccessible(AccessibleObject.java:354)
	at java.base/java.lang.reflect.AccessibleObject.checkCanSetAccessible(AccessibleObject.java:297)
	at java.base/java.lang.reflect.Field.checkCanSetAccessible(Field.java:178)
	at java.base/java.lang.reflect.Field.setAccessible(Field.java:172)
	at org.wildfly.security.manager.GetAccessibleDeclaredFieldAction.run(GetAccessibleDeclaredFieldAction.java:52)
	at org.wildfly.security.manager.GetAccessibleDeclaredFieldAction.run(GetAccessibleDeclaredFieldAction.java:30)
	at java.base/java.security.AccessController.doPrivileged(AccessController.java:318)
	at org.wildfly.security.manager.WildFlySecurityManager.<clinit>(WildFlySecurityManager.java:109)
	... 16 more







import javax.ejb.Stateless;

/**
 * Session Bean implementation class FirstBean
 */
@Stateless
public class FirstBean implements FirstBeanRemote {

    /**
     * Default constructor. 
     */
    public FirstBean() {
        // TODO Auto-generated constructor stub
    }

	@Override
	public String myMetha() {
		// TODO Auto-generated method stub
		return "Welcome to EJB";
	}

}





package com.ejb.ser.sat;

import javax.ejb.Remote;

@Remote
public interface FirstBeanRemote {
	public String myMetha();
}




//////
package com.satejb.ser;

import javax.ejb.Remote;

@Remote
public interface SecBeanRemote {
	public String retCaps(String c);
}
/////
package com.satejb.ser;

import javax.ejb.LocalBean;
import javax.ejb.Stateless;

/**
 * Session Bean implementation class SecBean
 */
@Stateless
public class SecBean implements SecBeanRemote {

    public SecBean() {
    }

	@Override
	public String retCaps(String c) {
		return c.toUpperCase();
	}    
}
/////
package com.satejb.client;

import java.util.Properties;

import javax.naming.Context;
import javax.naming.InitialContext;
import javax.naming.NamingException;

import com.satejb.ser.SecBean;
import com.satejb.ser.SecBeanRemote;

public class MnClsA {

	public static void main(String[] args) throws NamingException {
		SecBeanRemote sc=EJBContextFactory.retBean("ejb:");
		String u=sc.retCaps("satish");
		System.out.println(u);
	}
	
	
	private static class EJBContextFactory{
		private static SecBeanRemote retBean(String namespace) throws NamingException {
			return retLookUp(namespace);
		}
		
		private static SecBeanRemote retLookUp(String namespace) throws NamingException {
			Context ctx=creaInitContext();
			String appName="";
			String moduleName="UnisysSecProj";
			String distinctName="";
			String beanName=SecBean.class.getSimpleName();
			String viewClassName=SecBeanRemote.class.getName();
			return (SecBeanRemote)ctx.lookup(namespace+appName+"/"+moduleName+"/"+distinctName+"/"+beanName+"!"+viewClassName);
		}
		
		private static Context creaInitContext() throws NamingException {
			Properties props=new Properties();
			props.put(Context.INITIAL_CONTEXT_FACTORY, "org.jboss.naming.remote.client.InitialContextFactory");
			props.put(Context.URL_PKG_PREFIXES, "org.jboss.ejb.client.naming");
			props.put(Context.PROVIDER_URL, "http-remoting://localhost:8080");
			props.put("jboss.naming.client.ejb.context", true);
			return new InitialContext(props);
		}
	}
}
//////
https://www.transfernow.net/en
//////

package c.ser.cls;

import javax.ejb.LocalBean;
import javax.ejb.Stateless;

/**
 * Session Bean implementation class MyBean
 */
@Stateless
public class MyBean implements MyBeanRemote {
    public MyBean() {
    }

	@Override
	public String myTest() {
		return "Radha Krishna";
	}

}
/////
package a.b.c;

import java.io.IOException;
import java.io.PrintWriter;

import javax.ejb.EJB;
import javax.naming.NamingException;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

import c.ser.cls.MyBean;

/**
 * Servlet implementation class NServe
 */
@WebServlet("/NServe")
public class NServe extends HttpServlet {
	private static final long serialVersionUID = 1L;
       

    /**
     * @see HttpServlet#HttpServlet()
     */
    public NServe() {
        super();
        // TODO Auto-generated constructor stub
    }

	/**
	 * @see HttpServlet#doGet(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		PrintWriter out=response.getWriter();
		out.println("Running the client");
	}

	/**
	 * @see HttpServlet#doPost(HttpServletRequest request, HttpServletResponse response)
	 */
	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		doGet(request, response);
	}

}
////
package a.b.c;

import java.util.Properties;

import javax.naming.Context;
import javax.naming.InitialContext;
import javax.naming.NamingException;

import c.ser.cls.MyBean;
import c.ser.cls.MyBeanRemote;

public class ClsEjb {
	public static void main(String[] args) throws NamingException {
		MyBeanRemote sc=EJBContextFactory.retBean("ejb:");
		String u=sc.myTest();
		System.out.println(u);
	}
	
	
	
	private static class EJBContextFactory{
		private static MyBeanRemote retBean(String namespace) throws NamingException {
			return retLookUp(namespace);
		}
		
		private static MyBeanRemote retLookUp(String namespace) throws NamingException {
			Context ctx=creaInitContext();
			String appName="";
			String moduleName="UnisysThirdProj";
			String distinctName="";
			String beanName=MyBean.class.getSimpleName();
			String viewClassName=MyBeanRemote.class.getName();
			return (MyBeanRemote)ctx.lookup(namespace+appName+"/"+moduleName+"/"+distinctName+"/"+beanName+"!"+viewClassName);
		}
		
		private static Context creaInitContext() throws NamingException {
			Properties props=new Properties();
			props.put(Context.INITIAL_CONTEXT_FACTORY, "org.jboss.naming.remote.client.InitialContextFactory");
			props.put(Context.URL_PKG_PREFIXES, "org.jboss.ejb.client.naming");
			props.put(Context.PROVIDER_URL, "http-remoting://localhost:8080");
			props.put("jboss.naming.client.ejb.context", true);
			return new InitialContext(props);
		}
	}
}
/////
package a.b.c;

import java.awt.Container;
import java.util.Properties;

import javax.naming.Context;
import javax.naming.InitialContext;
import javax.naming.NamingException;
import javax.swing.JFrame;
import javax.swing.JLabel;

import c.ser.cls.MyBean;
import c.ser.cls.MyBeanRemote;

public class MyFrame extends JFrame {
	public MyFrame() {
		Container cnt = getContentPane();
		JLabel lab = new JLabel();
		MyBeanRemote sc;
		try {
			sc = EJBContextFactory.retBean("ejb:");
			String u = sc.myTest();
			lab.setText(u);
			cnt.add(lab);
		} catch (NamingException e) {
			e.printStackTrace();
		}

	}

	private static class EJBContextFactory {
		private static MyBeanRemote retBean(String namespace) throws NamingException {
			return retLookUp(namespace);
		}

		private static MyBeanRemote retLookUp(String namespace) throws NamingException {
			Context ctx = creaInitContext();
			String appName = "";
			String moduleName = "UnisysThirdProj";
			String distinctName = "";
			String beanName = MyBean.class.getSimpleName();
			String viewClassName = MyBeanRemote.class.getName();
			return (MyBeanRemote) ctx.lookup(
					namespace + appName + "/" + moduleName + "/" + distinctName + "/" + beanName + "!" + viewClassName);
		}

		private static Context creaInitContext() throws NamingException {
			Properties props = new Properties();
			props.put(Context.INITIAL_CONTEXT_FACTORY, "org.jboss.naming.remote.client.InitialContextFactory");
			props.put(Context.URL_PKG_PREFIXES, "org.jboss.ejb.client.naming");
			props.put(Context.PROVIDER_URL, "http-remoting://localhost:8080");
			props.put("jboss.naming.client.ejb.context", true);
			return new InitialContext(props);
		}
	}
}
/////
package a.b.c;

import java.awt.FlowLayout;
import java.util.Properties;

import javax.naming.Context;
import javax.naming.InitialContext;
import javax.naming.NamingException;

import c.ser.cls.MyBean;
import c.ser.cls.MyBeanRemote;

public class ClsEjb {
	public static void main(String[] args) throws NamingException {
		MyFrame frame=new MyFrame();
		frame.setDefaultCloseOperation(2);
		frame.setVisible(true);
		frame.setSize(150, 150);
		frame.setLayout(new FlowLayout());
	}	
}
//////
/subsystem=security/security-domain=other/authentication=classic/login-module=RealmDirect:map-put(name=module-options,key=unauthenticatedIdentity,value=guest)

//////
package pp.qq.rr;

import java.util.Properties;

import javax.naming.Context;
import javax.naming.InitialContext;
import javax.naming.NamingException;

import com.sat.ejbse.CBean;
import com.sat.ejbse.CBeanRemote;

public class MnCls {

	public static void main(String[] args) throws NamingException {
		CBeanRemote cr=EJBContextFactory.retBean("ejb:");
		System.out.println(cr.retRev("Satish"));
System.out.println(cr.retRoot(21));
		
	}
	private static class EJBContextFactory {
		private static CBeanRemote retBean(String namespace) throws NamingException {
			return retLookUp(namespace);
		}

		private static CBeanRemote retLookUp(String namespace) throws NamingException {
			Context ctx = creaInitContext();
			String appName = "";
			String moduleName = "UnisysFourthProj";
			String distinctName = "";
			String beanName = CBean.class.getSimpleName();
			String viewClassName = CBeanRemote.class.getName();
			return (CBeanRemote) ctx.lookup(
					namespace + appName + "/" + moduleName + "/" + distinctName + "/" + beanName + "!" + viewClassName);
		}

		private static Context creaInitContext() throws NamingException {
			Properties props = new Properties();
			props.put(Context.INITIAL_CONTEXT_FACTORY, "org.jboss.naming.remote.client.InitialContextFactory");
			props.put(Context.URL_PKG_PREFIXES, "org.jboss.ejb.client.naming");
			props.put(Context.PROVIDER_URL, "http-remoting://localhost:8080");
			props.put("jboss.naming.client.ejb.context", true);
			return new InitialContext(props);
		}
	}
}


/////
package com.sat.ejbse;

import javax.ejb.Remote;

@Remote
public interface CBeanRemote {
	public String retRev(String b);
	public double retRoot(int i);
}
//////
package com.sat.ejbse;

import javax.ejb.LocalBean;
import javax.ejb.Stateless;

/**
 * Session Bean implementation class CBean
 */
@Stateless
public class CBean implements CBeanRemote {
    public CBean() {
    }

	@Override
	public String retRev(String b) {
		StringBuffer buf=new StringBuffer(b);
		String j=buf.reverse().toString();
		return j;
	}

	@Override
	public double retRoot(int i) {
		return Math.sqrt(i);
	}
}
/////
package pp.qq.rr;

import java.awt.Container;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.util.Properties;
import java.util.Vector;

import javax.naming.Context;
import javax.naming.InitialContext;
import javax.naming.NamingException;
import javax.swing.JComboBox;
import javax.swing.JFrame;

import com.sat.ejbse.CBean;
import com.sat.ejbse.CBeanRemote;



public class MyFrame extends JFrame {

	public MyFrame() throws NamingException {
		Container cont=getContentPane();
		Vector vec=new Vector();
		CBeanRemote cr=EJBContextFactory.retBean("ejb:");
		for (int i = 1; i < 101; i++) {
			vec.add(cr.retRoot(i));
		}
		JComboBox box=new JComboBox(vec);
		cont.add(box);
	}
	
	private static class EJBContextFactory {
		private static CBeanRemote retBean(String namespace) throws NamingException {
			return retLookUp(namespace);
		}

		private static CBeanRemote retLookUp(String namespace) throws NamingException {
			Context ctx = creaInitContext();
			String appName = "";
			String moduleName = "UnisysFourthProj";
			String distinctName = "";
			String beanName = CBean.class.getSimpleName();
			String viewClassName = CBeanRemote.class.getName();
			return (CBeanRemote) ctx.lookup(
					namespace + appName + "/" + moduleName + "/" + distinctName + "/" + beanName + "!" + viewClassName);
		}

		private static Context creaInitContext() throws NamingException {
			Properties props = new Properties();
			props.put(Context.INITIAL_CONTEXT_FACTORY, "org.jboss.naming.remote.client.InitialContextFactory");
			props.put(Context.URL_PKG_PREFIXES, "org.jboss.ejb.client.naming");
			props.put(Context.PROVIDER_URL, "http-remoting://localhost:8080");
			props.put("jboss.naming.client.ejb.context", true);
			return new InitialContext(props);
		}
	}
	
	
	
}

/////
public static void main(String[] args) throws NamingException {
		MyFrame frame=new MyFrame();
		frame.setDefaultCloseOperation(2);
		frame.setVisible(true);
		frame.setSize(1000,1000);
		frame.setLayout(new FlowLayout());
		
		//		CBeanRemote cr=EJBContextFactory.retBean("ejb:");
//		System.out.println(cr.retRev("Satish"));
//		System.out.println(cr.retRoot(21));
//		int a=0;
//		Scanner scan=new Scanner(System.in);
//		System.out.println("Enter a number whose sigma needs to be calculated");
//		a=scan.nextInt();
//		System.out.println(cr.retSumTill(a));
//		
	}

//////servlet.txt////
Servlet is a java program that runs inside JVM on the web server. It is used for developing dynamic web applications.
Before we proceed further lets understand what is dynamic web application? A web application can be described as collection of web pages (e.g. a website) and when we call it dynamic, it simply means that the web pages are not same for all the users, web pages would be generated on server side based on the request made by client(user’s browser).

Every Servlet must implement the java.servlet.Servlet interface, you can do it by extending one of the following two classes: javax.servlet.GenericServlet or javax.servlet.http.HttpServlet. The first one is for protocol independent Servlet and the second one for http Servlet.[Bootstrap]

Angular->TypeScript[Front end technology which is based on MVC]->Google
React->View Library Created by Facebook->Javascript latest...[Ecmascript]->javascript
[Vuejs]->javascript
[Knockout]->javascript
[Flask]->Python
[Ruby On Rails]->Ruby[Grails]


If you creating Http Servlet you must extend javax.servlet.http.HttpServlet class, which is an abstract class. Unlike Generic Servlet, the HTTP Servlet doesn’t override the service() method. Instead it overrides one or more of the following methods. It must override at least one method from the list below:
doGet() – This method is called by servlet service method to handle the HTTP GET request from client. The Get method is used for getting information from the server
doPost() – Used for posting information to the Server
doPut() – This method is similar to doPost method but unlike doPost method where we send information to the server, this method sends file to the server, this is similar to the FTP operation from client to server
doDelete() – allows a client to delete a document, webpage or information from the server
init() and destroy() – Used for managing resources that are held for the life of the servlet
getServletInfo() – Returns information about the servlet, such as author, version, and copyright.
Interfaces in javax.servlet
Servlet
ServletRequest
ServletResponse
ServletConfig
ServletContext
SingleThreadModel
RequestDispatcher
ServletRequestListener
ServletRequestAttributeListener
ServletContextListener
ServletContextAttributeListener
Filter
FilterConfig
FilterChain
Classes in javax.servlet package
GenericServlet
ServletInputStream
ServletOutputStream
ServletException
ServletRequestWrapper
ServletRequestEvent
ServletResponseWrapper
ServletContextEvent
ServletRequestAttributeEvent
ServletContextAttributeEvent
UnavailableException


TTF=True Type Font=This is the only printable font[Verdana,Arial,Georgia,Helvetica, consolas ]
/////////////
package com.sat.serva;

import javax.ejb.Remote;

@Remote
public interface FileBeanARemote {
	public String retContents();
	public String retBook();
}

/////
package com.sat.serva;

import java.io.File;
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;

import javax.ejb.LocalBean;
import javax.ejb.Stateless;

/**
 * Session Bean implementation class FileBeanA
 */
@Stateless
@LocalBean
public class FileBeanA implements FileBeanARemote {
	private final String fname="C:\\DelhiOfficeFiles\\ServletNotes.txt";
    public FileBeanA() {
    }

	@Override
	public String retContents() {
		File f=new File(fname);
		String fCont="";
		try {
			FileInputStream fis=new FileInputStream(f);
			int i=0;
			while((i=fis.read())!=-1) {
				fCont+=(char)i;
			}
			fis.close();
		} catch (FileNotFoundException e) {
			e.printStackTrace();
		} catch (IOException e) {
			e.printStackTrace();
		}
		return fCont;
	}

	@Override
	public String retBook() {
		Books b=new Books();
		b.setBid(1223);
		b.setBname("Meghasandesam");
		b.setBauth("Mahakavi Kalidasa");
		return b.getBid()+" "+b.getBname()+" "+b.getBauth();
	}

}
//////
https://livebook.manning.com/book/junit-in-action-second-edition/chapter-14/31
/////
package com.sat.clienta;

import java.util.Properties;

import javax.naming.Context;
import javax.naming.InitialContext;
import javax.naming.NamingException;

import com.sat.serva.FileBeanA;
import com.sat.serva.FileBeanARemote;

public class MnClsClient {

	public static void main(String[] args) throws NamingException {
		FileBeanARemote fa=EJBContextFactory.retBean("ejb:");
		String u=fa.retContents();
		System.err.println(u);
		String b=fa.retBook();
		System.out.println(b);
	}
	
	private static class EJBContextFactory {
		private static FileBeanARemote retBean(String namespace) throws NamingException {
			return retLookUp(namespace);
		}

		private static FileBeanARemote retLookUp(String namespace) throws NamingException {
			Context ctx = creaInitContext();
			String appName = "";
			String moduleName = "UnisysFifthProj";
			String distinctName = "";
			String beanName = FileBeanA.class.getSimpleName();
			String viewClassName = FileBeanARemote.class.getName();
			return (FileBeanARemote) ctx.lookup(
					namespace + appName + "/" + moduleName + "/" + distinctName + "/" + beanName + "!" + viewClassName);
		}

		private static Context creaInitContext() throws NamingException {
			Properties props = new Properties();
			props.put(Context.INITIAL_CONTEXT_FACTORY, "org.jboss.naming.remote.client.InitialContextFactory");
			props.put(Context.URL_PKG_PREFIXES, "org.jboss.ejb.client.naming");
			props.put(Context.PROVIDER_URL, "http-remoting://localhost:8080");
			props.put("jboss.naming.client.ejb.context", true);
			return new InitialContext(props);
		}
	}
	

}
//////
package com.sat.serva;

public class Books {
	private int bid;
	public int getBid() {
		return bid;
	}
	public void setBid(int bid) {
		this.bid = bid;
	}
	public String getBname() {
		return bname;
	}
	public void setBname(String bname) {
		this.bname = bname;
	}
	public String getBauth() {
		return bauth;
	}
	public void setBauth(String bauth) {
		this.bauth = bauth;
	}
	private String bname;
	private String bauth;
}
/////
<module xmlns="urn:jboss:module:1.1" name="com.mysql">
  <resources>
    <resource-root path="mysql-connector-java-5.0.5.jar"/>
  </resources>
  <dependencies>
    <module name="javax.api"/>
    <module name="javax.transaction.api"/>
  </dependencies>
</module>


/////
Labs.novelvista.com	JAVA-11	1tRrGdWHq
/////
<driver name="mysql" module="com.mysql">
                        <driver-class>com.mysql.jdbc.Driver</driver-class>
                        <xa-datasource-class>com.mysql.cj.jdbc.MysqlXADataSource</xa-datasource-class>
                    </driver>
/////
                <datasource jndi-name="java:jboss/MySqlDS" pool-name="MySqlDS">
                    <connection-url>jdbc:mysql://localhost:3306/sopraserve?characterEncoding=UTF8</connection-url>
                    <driver>mysql</driver>
                    <security>
                        <user-name>root</user-name>
                        <password>admin</password>
                    </security>
                </datasource>

/////
Stateful Session preserve the conversational state with client.
Jboss stateful session it creates one instance for each request of the client.
It only lasts till the session lasts.
Business logic

/////16/05/2024/////
package com.sata.serve;

import javax.ejb.Remote;

@Remote
public interface MySBeanRemote {
	public String retSecLetterCaps(String a);
}
////
package com.sata.serve;

import javax.ejb.LocalBean;
import javax.ejb.Stateful;

/**
 * Session Bean implementation class MySBean
 */
@Stateful
public class MySBean implements MySBeanRemote {

    public MySBean() {
    }

	@Override
	public String retSecLetterCaps(String a) {
		char[] arr=a.toCharArray();
		String u="";
		int i=1;
		for(char c:arr) {
			if(i%2==0) {
				u+=String.valueOf(c).toUpperCase();
			}else {
				u+=String.valueOf(c);
			}
			i++;
		}
		return u;
	}
}


/////
package co.sa.cli;

import java.util.Properties;

import javax.naming.Context;
import javax.naming.InitialContext;
import javax.naming.NamingException;

import com.sata.serve.MySBean;
import com.sata.serve.MySBeanRemote;

public class MainCls {
	public static void main(String[] args) throws NamingException {
		MySBeanRemote msb=EJBContext.retBean("ejb:");
		String j=msb.retSecLetterCaps("this is rather a long string to be a part of parameter");
		System.out.println(j);
	}

	private static class EJBContext {
		private static MySBeanRemote retBean(String namespace) throws NamingException {
			return retLookUp(namespace);
		}

		private static MySBeanRemote retLookUp(String namespace) throws NamingException {
			Context ctx = creaInitContext();
			String appName = "";
			String moduleName = "UnisysSixthProj";
			String distinctName = "";
			String beanName = MySBean.class.getSimpleName();
			String viewClassName = MySBeanRemote.class.getName();
			return (MySBeanRemote) ctx.lookup(namespace + appName + "/" + moduleName + "/" + distinctName + "/"
					+ beanName + "!" + viewClassName + "?stateful");
		}

		private static Context creaInitContext() throws NamingException {
			Properties props = new Properties();
			props.put(Context.INITIAL_CONTEXT_FACTORY, "org.jboss.naming.remote.client.InitialContextFactory");
			props.put(Context.URL_PKG_PREFIXES, "org.jboss.ejb.client.naming");
			props.put(Context.PROVIDER_URL, "http-remoting://localhost:8080");
			props.put("jboss.naming.client.ejb.context", true);
			return new InitialContext(props);
		}
	}
}
//////


Bound data source [java:jboss/MySqlDS]

/////
package com.satb.serve;

public interface IVals {
	public static final String fname="C:\\DelhiOfficeFiles\\unisysdata.txt";
}

////
package com.satb.serve;

import javax.ejb.Remote;

@Remote
public interface ABeanStateRemote {
	public String wrFile(String conts);
}
/////
package com.satb.serve;

import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;

import javax.ejb.LocalBean;
import javax.ejb.Stateful;


@Stateful
public class ABeanState implements ABeanStateRemote,IVals {

    public ABeanState() {
    }

	@Override
	public String wrFile(String conts) {
		File f=new File(fname);
		String status="not done";
		try {
			FileOutputStream fos=new FileOutputStream(f,true);
			fos.write(conts.getBytes());
			fos.flush();
			fos.close();
			status="done";
		} catch (FileNotFoundException e) {
			e.printStackTrace();
		} catch (IOException e) {
			e.printStackTrace();
		}		
		return status;
	}
}
////
String[] strs=new String[] {"Physics","Nuclear Physics","Geo Physics"};
		System.out.println(Arrays.deepToString(strs));
//////
package co.sa.clia;

public class Person {
	private String pname;
	private String pemail;
	private String pmobile;
	public Person() {
	}
	public Person(String a,String b,String c) {
		this.pname=a;
		this.pemail=b;
		this.pmobile=c;
	}
	@Override
	public String toString() {
		String fin=String.format("Name:%s Email: %s Mobile:%s", this.pname,this.pemail,this.pmobile);
		return fin;
	}
}
/////
package co.sa.clia;

import java.util.Arrays;
import java.util.Properties;
import java.util.Scanner;

import javax.naming.Context;
import javax.naming.InitialContext;
import javax.naming.NamingException;

import com.satb.serve.ABeanState;
import com.satb.serve.ABeanStateRemote;

public class MnClsA {

	public static void main(String[] args) throws NamingException {
		Person[] pArr=new Person[5];
		Scanner scan=new Scanner(System.in);
		int i=0;
		while(i<5) {
			System.out.println("Enter the name of the person");
			String name=scan.nextLine();
			System.out.println("Enter the email of the person");
			String email=scan.nextLine();
			System.out.println("Enter the mobile of the person");
			String mobile=scan.nextLine();
			Person pObj=new Person(name, email, mobile);
			pArr[i]=pObj;
			i++;
		}
		String resp=Arrays.deepToString(pArr);
		ABeanStateRemote abs=EJBContext.retBean("ejb:");
		abs.wrFile(resp);
	}
	
	private static class EJBContext{
		private static ABeanStateRemote retBean(String namespace) throws NamingException {
			return retLookUp(namespace);
		}

		private static ABeanStateRemote retLookUp(String namespace) throws NamingException {
			Context ctx = creaInitContext();
			String appName = "";
			String moduleName = "UnisysSeventhProj";
			String distinctName = "";
			String beanName = ABeanState.class.getSimpleName();
			String viewClassName = ABeanStateRemote.class.getName();
			return (ABeanStateRemote) ctx.lookup(namespace + appName + "/" + moduleName + "/" + distinctName + "/"
					+ beanName + "!" + viewClassName + "?stateful");
		}

		private static Context creaInitContext() throws NamingException {
			Properties props = new Properties();
			props.put(Context.INITIAL_CONTEXT_FACTORY, "org.jboss.naming.remote.client.InitialContextFactory");
			props.put(Context.URL_PKG_PREFIXES, "org.jboss.ejb.client.naming");
			props.put(Context.PROVIDER_URL, "http-remoting://localhost:8080");
			props.put("jboss.naming.client.ejb.context", true);
			return new InitialContext(props);
		}
	}
}
/////
create table persons(id int primary key,name varchar(50),dept varchar(50));
//////
insert into persons values(10,'Reena','Receptionist');
/////
package com.sat.serveb;

import javax.ejb.Remote;

@Remote
public interface DbBeanARemote {
		public String retConts();
}
//////
package com.sat.serveb;

import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

import javax.ejb.LocalBean;
import javax.ejb.Stateful;
import javax.naming.InitialContext;
import javax.naming.NamingException;
import javax.sql.DataSource;

/**
 * Session Bean implementation class DbBeanA
 */
@Stateful
@LocalBean
public class DbBeanA implements DbBeanARemote {
    public DbBeanA() {
    }

	@Override
	public String retConts() {
		String res="";
		try {
			DataSource ds=(DataSource)(new InitialContext().lookup("java:jboss/MySqlDS"));
			Connection conn=ds.getConnection();
			Statement st=conn.createStatement();
			ResultSet rs=st.executeQuery("select * from persons");
			
			while(rs.next()) {
				res+=rs.getInt(1)+"-"+rs.getString(2)+"-"+rs.getString(3)+";";
			}
		} catch (NamingException e) {
			e.printStackTrace();
		} catch (SQLException e) {
			e.printStackTrace();
		}
		return res;
	}

    
    
    
}
/////
package co.sa.da.cli;

import java.util.Properties;
import java.util.StringTokenizer;

import javax.naming.Context;
import javax.naming.InitialContext;
import javax.naming.NamingException;

import com.sat.serveb.DbBeanA;
import com.sat.serveb.DbBeanARemote;

public class MyClientCls {
	public static void main(String[] args) throws NamingException {
		DbBeanARemote dbr=EJBContext.retBean("ejb:");
		String res=dbr.retConts();
//		System.out.println(res);
		StringTokenizer str=new StringTokenizer(res, ";");
		while(str.hasMoreTokens()) {
			String u[]=str.nextToken().toString().split("-");
			for(String k:u) {
				System.out.println(k);
			}
			System.out.println("***********************");
			//System.out.println(str.nextToken().toString());
		}
	}
	
	private static class EJBContext{
		private static DbBeanARemote retBean(String namespace) throws NamingException {
			return retLookUp(namespace);
		}

		private static DbBeanARemote retLookUp(String namespace) throws NamingException {
			Context ctx = creaInitContext();
			String appName = "";
			String moduleName = "UnisysEighthProj";
			String distinctName = "";
			String beanName = DbBeanA.class.getSimpleName();
			String viewClassName = DbBeanARemote.class.getName();
			return (DbBeanARemote) ctx.lookup(namespace + appName + "/" + moduleName + "/" + distinctName + "/"
					+ beanName + "!" + viewClassName + "?stateful");
		}

		private static Context creaInitContext() throws NamingException {
			Properties props = new Properties();
			props.put(Context.INITIAL_CONTEXT_FACTORY, "org.jboss.naming.remote.client.InitialContextFactory");
			props.put(Context.URL_PKG_PREFIXES, "org.jboss.ejb.client.naming");
			props.put(Context.PROVIDER_URL, "http-remoting://localhost:8080");
			props.put("jboss.naming.client.ejb.context", true);
			return new InitialContext(props);
		}
	}
	
	
}

//////
<?xml version='1.0' encoding='UTF-8'?>

<server xmlns="urn:jboss:domain:5.0">
    <extensions>
        <extension module="org.jboss.as.clustering.infinispan"/>
        <extension module="org.jboss.as.connector"/>
        <extension module="org.jboss.as.deployment-scanner"/>
        <extension module="org.jboss.as.ee"/>
        <extension module="org.jboss.as.ejb3"/>
        <extension module="org.jboss.as.jaxrs"/>
        <extension module="org.jboss.as.jdr"/>
        <extension module="org.jboss.as.jmx"/>
        <extension module="org.jboss.as.jpa"/>
        <extension module="org.jboss.as.jsf"/>
        <extension module="org.jboss.as.jsr77"/>
        <extension module="org.jboss.as.logging"/>
        <extension module="org.jboss.as.mail"/>
        <extension module="org.jboss.as.naming"/>
        <extension module="org.jboss.as.pojo"/>
        <extension module="org.jboss.as.remoting"/>
        <extension module="org.jboss.as.sar"/>
        <extension module="org.jboss.as.security"/>
        <extension module="org.jboss.as.transactions"/>
        <extension module="org.jboss.as.webservices"/>
        <extension module="org.jboss.as.weld"/>
        <extension module="org.wildfly.extension.batch.jberet"/>
        <extension module="org.wildfly.extension.bean-validation"/>
        <extension module="org.wildfly.extension.core-management"/>
        <extension module="org.wildfly.extension.elytron"/>
        <extension module="org.wildfly.extension.io"/>
        <extension module="org.wildfly.extension.messaging-activemq"/>
        <extension module="org.wildfly.extension.request-controller"/>
        <extension module="org.wildfly.extension.security.manager"/>
        <extension module="org.wildfly.extension.undertow"/>
        <extension module="org.wildfly.iiop-openjdk"/>
    </extensions>
    <management>
        <security-realms>
            <security-realm name="ManagementRealm">
                <authentication>
                    <local default-user="$local" skip-group-loading="true"/>
                    <properties path="mgmt-users.properties" relative-to="jboss.server.config.dir"/>
                </authentication>
                <authorization map-groups-to-roles="false">
                    <properties path="mgmt-groups.properties" relative-to="jboss.server.config.dir"/>
                </authorization>
            </security-realm>
            <security-realm name="ApplicationRealm">
                <server-identities>
                    <ssl>
                        <keystore path="application.keystore" relative-to="jboss.server.config.dir" keystore-password="password" alias="server" key-password="password" generate-self-signed-certificate-host="localhost"/>
                    </ssl>
                </server-identities>
                <authentication>
                    <local default-user="$local" allowed-users="*" skip-group-loading="true"/>
                    <properties path="application-users.properties" relative-to="jboss.server.config.dir"/>
                </authentication>
                <authorization>
                    <properties path="application-roles.properties" relative-to="jboss.server.config.dir"/>
                </authorization>
            </security-realm>
        </security-realms>
        <audit-log>
            <formatters>
                <json-formatter name="json-formatter"/>
            </formatters>
            <handlers>
                <file-handler name="file" formatter="json-formatter" path="audit-log.log" relative-to="jboss.server.data.dir"/>
            </handlers>
            <logger log-boot="true" log-read-only="false" enabled="false">
                <handlers>
                    <handler name="file"/>
                </handlers>
            </logger>
        </audit-log>
        <management-interfaces>
            <http-interface security-realm="ManagementRealm">
                <http-upgrade enabled="true"/>
                <socket-binding http="management-http"/>
            </http-interface>
        </management-interfaces>
        <access-control provider="simple">
            <role-mapping>
                <role name="SuperUser">
                    <include>
                        <user name="$local"/>
                    </include>
                </role>
            </role-mapping>
        </access-control>
    </management>
    <profile>
        <subsystem xmlns="urn:jboss:domain:logging:3.0">
            <console-handler name="CONSOLE">
                <level name="INFO"/>
                <formatter>
                    <named-formatter name="COLOR-PATTERN"/>
                </formatter>
            </console-handler>
            <periodic-rotating-file-handler name="FILE" autoflush="true">
                <formatter>
                    <named-formatter name="PATTERN"/>
                </formatter>
                <file relative-to="jboss.server.log.dir" path="server.log"/>
                <suffix value=".yyyy-MM-dd"/>
                <append value="true"/>
            </periodic-rotating-file-handler>
            <logger category="com.arjuna">
                <level name="WARN"/>
            </logger>
            <logger category="org.jboss.as.config">
                <level name="DEBUG"/>
            </logger>
            <logger category="sun.rmi">
                <level name="WARN"/>
            </logger>
            <root-logger>
                <level name="INFO"/>
                <handlers>
                    <handler name="CONSOLE"/>
                    <handler name="FILE"/>
                </handlers>
            </root-logger>
            <formatter name="PATTERN">
                <pattern-formatter pattern="%d{yyyy-MM-dd HH:mm:ss,SSS} %-5p [%c] (%t) %s%e%n"/>
            </formatter>
            <formatter name="COLOR-PATTERN">
                <pattern-formatter pattern="%K{level}%d{HH:mm:ss,SSS} %-5p [%c] (%t) %s%e%n"/>
            </formatter>
        </subsystem>
        <subsystem xmlns="urn:jboss:domain:batch-jberet:2.0">
            <default-job-repository name="in-memory"/>
            <default-thread-pool name="batch"/>
            <job-repository name="in-memory">
                <in-memory/>
            </job-repository>
            <thread-pool name="batch">
                <max-threads count="10"/>
                <keepalive-time time="30" unit="seconds"/>
            </thread-pool>
        </subsystem>
        <subsystem xmlns="urn:jboss:domain:bean-validation:1.0"/>
        <subsystem xmlns="urn:jboss:domain:core-management:1.0"/>
        <subsystem xmlns="urn:jboss:domain:datasources:5.0">
            <datasources>
                <datasource jndi-name="java:jboss/datasources/ExampleDS" pool-name="ExampleDS" enabled="true" use-java-context="true">
                    <connection-url>jdbc:h2:mem:test;DB_CLOSE_DELAY=-1;DB_CLOSE_ON_EXIT=FALSE</connection-url>
                    <driver>h2</driver>
                    <security>
                        <user-name>sa</user-name>
                        <password>sa</password>
                    </security>
                </datasource>
                <datasource jndi-name="java:jboss/MySqlDS" pool-name="MySqlDS">
                    <connection-url>jdbc:mysql://localhost:3306/unifirst?characterEncoding=UTF8</connection-url>
                    <driver>mysql</driver>
                    <security>
                        <user-name>root</user-name>
                        <password>unisys@1321</password>
                    </security>
                </datasource>
                <drivers>
                    <driver name="h2" module="com.h2database.h2">
                        <xa-datasource-class>org.h2.jdbcx.JdbcDataSource</xa-datasource-class>
                    </driver>
                    <driver name="mysql" module="com.mysql">
                        <driver-class>com.mysql.jdbc.Driver</driver-class>
                        <xa-datasource-class>com.mysql.cj.jdbc.MysqlXADataSource</xa-datasource-class>
                    </driver>
                </drivers>
            </datasources>
        </subsystem>
        <subsystem xmlns="urn:jboss:domain:deployment-scanner:2.0">
            <deployment-scanner path="deployments" relative-to="jboss.server.base.dir" scan-interval="5000" runtime-failure-causes-rollback="${jboss.deployment.scanner.rollback.on.failure:false}"/>
        </subsystem>
        <subsystem xmlns="urn:jboss:domain:ee:4.0">
            <spec-descriptor-property-replacement>false</spec-descriptor-property-replacement>
            <concurrent>
                <context-services>
                    <context-service name="default" jndi-name="java:jboss/ee/concurrency/context/default" use-transaction-setup-provider="true"/>
                </context-services>
                <managed-thread-factories>
                    <managed-thread-factory name="default" jndi-name="java:jboss/ee/concurrency/factory/default" context-service="default"/>
                </managed-thread-factories>
                <managed-executor-services>
                    <managed-executor-service name="default" jndi-name="java:jboss/ee/concurrency/executor/default" context-service="default" hung-task-threshold="60000" keepalive-time="5000"/>
                </managed-executor-services>
                <managed-scheduled-executor-services>
                    <managed-scheduled-executor-service name="default" jndi-name="java:jboss/ee/concurrency/scheduler/default" context-service="default" hung-task-threshold="60000" keepalive-time="3000"/>
                </managed-scheduled-executor-services>
            </concurrent>
            <default-bindings context-service="java:jboss/ee/concurrency/context/default" datasource="java:jboss/datasources/ExampleDS" jms-connection-factory="java:jboss/DefaultJMSConnectionFactory" managed-executor-service="java:jboss/ee/concurrency/executor/default" managed-scheduled-executor-service="java:jboss/ee/concurrency/scheduler/default" managed-thread-factory="java:jboss/ee/concurrency/factory/default"/>
        </subsystem>
        <subsystem xmlns="urn:jboss:domain:ejb3:5.0">
            <session-bean>
                <stateless>
                    <bean-instance-pool-ref pool-name="slsb-strict-max-pool"/>
                </stateless>
                <stateful default-access-timeout="5000" cache-ref="simple" passivation-disabled-cache-ref="simple"/>
                <singleton default-access-timeout="5000"/>
            </session-bean>
            <mdb>
                <resource-adapter-ref resource-adapter-name="${ejb.resource-adapter-name:activemq-ra.rar}"/>
                <bean-instance-pool-ref pool-name="mdb-strict-max-pool"/>
            </mdb>
            <pools>
                <bean-instance-pools>
                    <strict-max-pool name="slsb-strict-max-pool" derive-size="from-worker-pools" instance-acquisition-timeout="5" instance-acquisition-timeout-unit="MINUTES"/>
                    <strict-max-pool name="mdb-strict-max-pool" derive-size="from-cpu-count" instance-acquisition-timeout="5" instance-acquisition-timeout-unit="MINUTES"/>
                </bean-instance-pools>
            </pools>
            <caches>
                <cache name="simple"/>
                <cache name="distributable" passivation-store-ref="infinispan" aliases="passivating clustered"/>
            </caches>
            <passivation-stores>
                <passivation-store name="infinispan" cache-container="ejb" max-size="10000"/>
            </passivation-stores>
            <async thread-pool-name="default"/>
            <timer-service thread-pool-name="default" default-data-store="default-file-store">
                <data-stores>
                    <file-data-store name="default-file-store" path="timer-service-data" relative-to="jboss.server.data.dir"/>
                </data-stores>
            </timer-service>
            <remote connector-ref="http-remoting-connector" thread-pool-name="default">
                <channel-creation-options>
                    <option name="READ_TIMEOUT" value="${prop.remoting-connector.read.timeout:20}" type="xnio"/>
                    <option name="MAX_OUTBOUND_MESSAGES" value="1234" type="remoting"/>
                </channel-creation-options>
            </remote>
            <thread-pools>
                <thread-pool name="default">
                    <max-threads count="10"/>
                    <keepalive-time time="100" unit="milliseconds"/>
                </thread-pool>
            </thread-pools>
            <iiop enable-by-default="false" use-qualified-name="false"/>
            <default-security-domain value="other"/>
            <default-missing-method-permissions-deny-access value="true"/>
            <log-system-exceptions value="true"/>
        </subsystem>
        <subsystem xmlns="urn:wildfly:elytron:1.2" final-providers="combined-providers" disallowed-providers="OracleUcrypto">
            <providers>
                <aggregate-providers name="combined-providers">
                    <providers name="elytron"/>
                    <providers name="openssl"/>
                </aggregate-providers>
                <provider-loader name="elytron" module="org.wildfly.security.elytron"/>
                <provider-loader name="openssl" module="org.wildfly.openssl"/>
            </providers>
            <audit-logging>
                <file-audit-log name="local-audit" path="audit.log" relative-to="jboss.server.log.dir" format="JSON"/>
            </audit-logging>
            <security-domains>
                <security-domain name="ApplicationDomain" default-realm="ApplicationRealm" permission-mapper="default-permission-mapper">
                    <realm name="ApplicationRealm" role-decoder="groups-to-roles"/>
                    <realm name="local"/>
                </security-domain>
                <security-domain name="ManagementDomain" default-realm="ManagementRealm" permission-mapper="default-permission-mapper">
                    <realm name="ManagementRealm" role-decoder="groups-to-roles"/>
                    <realm name="local" role-mapper="super-user-mapper"/>
                </security-domain>
            </security-domains>
            <security-realms>
                <identity-realm name="local" identity="$local"/>
                <properties-realm name="ApplicationRealm">
                    <users-properties path="application-users.properties" relative-to="jboss.server.config.dir" digest-realm-name="ApplicationRealm"/>
                    <groups-properties path="application-roles.properties" relative-to="jboss.server.config.dir"/>
                </properties-realm>
                <properties-realm name="ManagementRealm">
                    <users-properties path="mgmt-users.properties" relative-to="jboss.server.config.dir" digest-realm-name="ManagementRealm"/>
                    <groups-properties path="mgmt-groups.properties" relative-to="jboss.server.config.dir"/>
                </properties-realm>
            </security-realms>
            <mappers>
                <simple-permission-mapper name="default-permission-mapper" mapping-mode="first">
                    <permission-mapping>
                        <principal name="anonymous"/>
                        <permission class-name="org.wildfly.extension.batch.jberet.deployment.BatchPermission" module="org.wildfly.extension.batch.jberet" target-name="*"/>
                        <permission class-name="org.wildfly.transaction.client.RemoteTransactionPermission" module="org.wildfly.transaction.client"/>
                        <permission class-name="org.jboss.ejb.client.RemoteEJBPermission" module="org.jboss.ejb-client"/>
                    </permission-mapping>
                    <permission-mapping match-all="true">
                        <permission class-name="org.wildfly.security.auth.permission.LoginPermission"/>
                        <permission class-name="org.wildfly.extension.batch.jberet.deployment.BatchPermission" module="org.wildfly.extension.batch.jberet" target-name="*"/>
                        <permission class-name="org.wildfly.transaction.client.RemoteTransactionPermission" module="org.wildfly.transaction.client"/>
                        <permission class-name="org.jboss.ejb.client.RemoteEJBPermission" module="org.jboss.ejb-client"/>
                    </permission-mapping>
                </simple-permission-mapper>
                <constant-realm-mapper name="local" realm-name="local"/>
                <simple-role-decoder name="groups-to-roles" attribute="groups"/>
                <constant-role-mapper name="super-user-mapper">
                    <role name="SuperUser"/>
                </constant-role-mapper>
            </mappers>
            <http>
                <http-authentication-factory name="management-http-authentication" http-server-mechanism-factory="global" security-domain="ManagementDomain">
                    <mechanism-configuration>
                        <mechanism mechanism-name="DIGEST">
                            <mechanism-realm realm-name="ManagementRealm"/>
                        </mechanism>
                    </mechanism-configuration>
                </http-authentication-factory>
                <http-authentication-factory name="application-http-authentication" http-server-mechanism-factory="global" security-domain="ApplicationDomain">
                    <mechanism-configuration>
                        <mechanism mechanism-name="BASIC">
                            <mechanism-realm realm-name="Application Realm"/>
                        </mechanism>
                        <mechanism mechanism-name="FORM"/>
                    </mechanism-configuration>
                </http-authentication-factory>
                <provider-http-server-mechanism-factory name="global"/>
            </http>
            <sasl>
                <sasl-authentication-factory name="management-sasl-authentication" sasl-server-factory="configured" security-domain="ManagementDomain">
                    <mechanism-configuration>
                        <mechanism mechanism-name="JBOSS-LOCAL-USER" realm-mapper="local"/>
                        <mechanism mechanism-name="DIGEST-MD5">
                            <mechanism-realm realm-name="ManagementRealm"/>
                        </mechanism>
                    </mechanism-configuration>
                </sasl-authentication-factory>
                <sasl-authentication-factory name="application-sasl-authentication" sasl-server-factory="configured" security-domain="ApplicationDomain">
                    <mechanism-configuration>
                        <mechanism mechanism-name="JBOSS-LOCAL-USER" realm-mapper="local"/>
                        <mechanism mechanism-name="DIGEST-MD5">
                            <mechanism-realm realm-name="ApplicationRealm"/>
                        </mechanism>
                    </mechanism-configuration>
                </sasl-authentication-factory>
                <configurable-sasl-server-factory name="configured" sasl-server-factory="elytron">
                    <properties>
                        <property name="wildfly.sasl.local-user.default-user" value="$local"/>
                    </properties>
                </configurable-sasl-server-factory>
                <mechanism-provider-filtering-sasl-server-factory name="elytron" sasl-server-factory="global">
                    <filters>
                        <filter provider-name="WildFlyElytron"/>
                    </filters>
                </mechanism-provider-filtering-sasl-server-factory>
                <provider-sasl-server-factory name="global"/>
            </sasl>
        </subsystem>
        <subsystem xmlns="urn:jboss:domain:io:2.0">
            <worker name="default"/>
            <buffer-pool name="default"/>
        </subsystem>
        <subsystem xmlns="urn:jboss:domain:infinispan:4.0">
            <cache-container name="server" default-cache="default" module="org.wildfly.clustering.server">
                <local-cache name="default">
                    <transaction mode="BATCH"/>
                </local-cache>
            </cache-container>
            <cache-container name="web" default-cache="passivation" module="org.wildfly.clustering.web.infinispan">
                <local-cache name="passivation">
                    <locking isolation="REPEATABLE_READ"/>
                    <transaction mode="BATCH"/>
                    <file-store passivation="true" purge="false"/>
                </local-cache>
            </cache-container>
            <cache-container name="ejb" aliases="sfsb" default-cache="passivation" module="org.wildfly.clustering.ejb.infinispan">
                <local-cache name="passivation">
                    <locking isolation="REPEATABLE_READ"/>
                    <transaction mode="BATCH"/>
                    <file-store passivation="true" purge="false"/>
                </local-cache>
            </cache-container>
            <cache-container name="hibernate" module="org.hibernate.infinispan">
                <local-cache name="entity">
                    <transaction mode="NON_XA"/>
                    <eviction strategy="LRU" max-entries="10000"/>
                    <expiration max-idle="100000"/>
                </local-cache>
                <local-cache name="local-query">
                    <eviction strategy="LRU" max-entries="10000"/>
                    <expiration max-idle="100000"/>
                </local-cache>
                <local-cache name="timestamps"/>
            </cache-container>
        </subsystem>
        <subsystem xmlns="urn:jboss:domain:iiop-openjdk:2.0">
            <orb socket-binding="iiop"/>
            <initializers security="identity" transactions="spec"/>
            <security server-requires-ssl="false" client-requires-ssl="false"/>
        </subsystem>
        <subsystem xmlns="urn:jboss:domain:jaxrs:1.0"/>
        <subsystem xmlns="urn:jboss:domain:jca:5.0">
            <archive-validation enabled="true" fail-on-error="true" fail-on-warn="false"/>
            <bean-validation enabled="true"/>
            <default-workmanager>
                <short-running-threads>
                    <core-threads count="50"/>
                    <queue-length count="50"/>
                    <max-threads count="50"/>
                    <keepalive-time time="10" unit="seconds"/>
                </short-running-threads>
                <long-running-threads>
                    <core-threads count="50"/>
                    <queue-length count="50"/>
                    <max-threads count="50"/>
                    <keepalive-time time="10" unit="seconds"/>
                </long-running-threads>
            </default-workmanager>
            <cached-connection-manager/>
        </subsystem>
        <subsystem xmlns="urn:jboss:domain:jdr:1.0"/>
        <subsystem xmlns="urn:jboss:domain:jmx:1.3">
            <expose-resolved-model/>
            <expose-expression-model/>
            <remoting-connector/>
        </subsystem>
        <subsystem xmlns="urn:jboss:domain:jpa:1.1">
            <jpa default-datasource="" default-extended-persistence-inheritance="DEEP"/>
        </subsystem>
        <subsystem xmlns="urn:jboss:domain:jsf:1.0"/>
        <subsystem xmlns="urn:jboss:domain:jsr77:1.0"/>
        <subsystem xmlns="urn:jboss:domain:mail:3.0">
            <mail-session name="default" jndi-name="java:jboss/mail/Default">
                <smtp-server outbound-socket-binding-ref="mail-smtp"/>
            </mail-session>
        </subsystem>
        <subsystem xmlns="urn:jboss:domain:messaging-activemq:2.0">
            <server name="default">
                <security-setting name="#">
                    <role name="guest" send="true" consume="true" create-non-durable-queue="true" delete-non-durable-queue="true"/>
                </security-setting>
                <address-setting name="#" dead-letter-address="jms.queue.DLQ" expiry-address="jms.queue.ExpiryQueue" max-size-bytes="10485760" page-size-bytes="2097152" message-counter-history-day-limit="10"/>
                <http-connector name="http-connector" socket-binding="http" endpoint="http-acceptor"/>
                <http-connector name="http-connector-throughput" socket-binding="http" endpoint="http-acceptor-throughput">
                    <param name="batch-delay" value="50"/>
                </http-connector>
                <in-vm-connector name="in-vm" server-id="0">
                    <param name="buffer-pooling" value="false"/>
                </in-vm-connector>
                <http-acceptor name="http-acceptor" http-listener="default"/>
                <http-acceptor name="http-acceptor-throughput" http-listener="default">
                    <param name="batch-delay" value="50"/>
                    <param name="direct-deliver" value="false"/>
                </http-acceptor>
                <in-vm-acceptor name="in-vm" server-id="0">
                    <param name="buffer-pooling" value="false"/>
                </in-vm-acceptor>
                <jms-queue name="ExpiryQueue" entries="java:/jms/queue/ExpiryQueue"/>
                <jms-queue name="DLQ" entries="java:/jms/queue/DLQ"/>
                <connection-factory name="InVmConnectionFactory" entries="java:/ConnectionFactory" connectors="in-vm"/>
                <connection-factory name="RemoteConnectionFactory" entries="java:jboss/exported/jms/RemoteConnectionFactory" connectors="http-connector"/>
                <pooled-connection-factory name="activemq-ra" entries="java:/JmsXA java:jboss/DefaultJMSConnectionFactory" connectors="in-vm" transaction="xa"/>
            </server>
        </subsystem>
        <subsystem xmlns="urn:jboss:domain:naming:2.0">
            <remote-naming/>
        </subsystem>
        <subsystem xmlns="urn:jboss:domain:pojo:1.0"/>
        <subsystem xmlns="urn:jboss:domain:remoting:4.0">
            <endpoint/>
            <http-connector name="http-remoting-connector" connector-ref="default" security-realm="ApplicationRealm"/>
        </subsystem>
        <subsystem xmlns="urn:jboss:domain:resource-adapters:5.0"/>
        <subsystem xmlns="urn:jboss:domain:request-controller:1.0"/>
        <subsystem xmlns="urn:jboss:domain:sar:1.0"/>
        <subsystem xmlns="urn:jboss:domain:security-manager:1.0">
            <deployment-permissions>
                <maximum-set>
                    <permission class="java.security.AllPermission"/>
                </maximum-set>
            </deployment-permissions>
        </subsystem>
        <subsystem xmlns="urn:jboss:domain:security:2.0">
            <security-domains>
                <security-domain name="other" cache-type="default">
                    <authentication>
                        <login-module code="Remoting" flag="optional">
                            <module-option name="password-stacking" value="useFirstPass"/>
                        </login-module>
                        <login-module code="RealmDirect" flag="required">
                            <module-option name="password-stacking" value="useFirstPass"/>
                        </login-module>
                    </authentication>
                </security-domain>
                <security-domain name="jboss-web-policy" cache-type="default">
                    <authorization>
                        <policy-module code="Delegating" flag="required"/>
                    </authorization>
                </security-domain>
                <security-domain name="jboss-ejb-policy" cache-type="default">
                    <authorization>
                        <policy-module code="Delegating" flag="required"/>
                    </authorization>
                </security-domain>
                <security-domain name="jaspitest" cache-type="default">
                    <authentication-jaspi>
                        <login-module-stack name="dummy">
                            <login-module code="Dummy" flag="optional"/>
                        </login-module-stack>
                        <auth-module code="Dummy"/>
                    </authentication-jaspi>
                </security-domain>
            </security-domains>
        </subsystem>
        <subsystem xmlns="urn:jboss:domain:transactions:4.0">
            <core-environment>
                <process-id>
                    <uuid/>
                </process-id>
            </core-environment>
            <recovery-environment socket-binding="txn-recovery-environment" status-socket-binding="txn-status-manager"/>
            <object-store path="tx-object-store" relative-to="jboss.server.data.dir"/>
        </subsystem>
        <subsystem xmlns="urn:jboss:domain:undertow:4.0">
            <buffer-cache name="default"/>
            <server name="default-server">
                <http-listener name="default" socket-binding="http" redirect-socket="https" enable-http2="true"/>
                <https-listener name="https" socket-binding="https" security-realm="ApplicationRealm" enable-http2="true"/>
                <host name="default-host" alias="localhost">
                    <location name="/" handler="welcome-content"/>
                    <filter-ref name="server-header"/>
                    <filter-ref name="x-powered-by-header"/>
                    <http-invoker security-realm="ApplicationRealm"/>
                </host>
            </server>
            <servlet-container name="default">
                <jsp-config/>
                <websockets/>
            </servlet-container>
            <handlers>
                <file name="welcome-content" path="${jboss.home.dir}/welcome-content"/>
            </handlers>
            <filters>
                <response-header name="server-header" header-name="Server" header-value="JBoss-EAP/7"/>
                <response-header name="x-powered-by-header" header-name="X-Powered-By" header-value="Undertow/1"/>
            </filters>
        </subsystem>
        <subsystem xmlns="urn:jboss:domain:webservices:2.0">
            <wsdl-host>${jboss.bind.address:127.0.0.1}</wsdl-host>
            <endpoint-config name="Standard-Endpoint-Config"/>
            <endpoint-config name="Recording-Endpoint-Config">
                <pre-handler-chain name="recording-handlers" protocol-bindings="##SOAP11_HTTP ##SOAP11_HTTP_MTOM ##SOAP12_HTTP ##SOAP12_HTTP_MTOM">
                    <handler name="RecordingHandler" class="org.jboss.ws.common.invocation.RecordingServerHandler"/>
                </pre-handler-chain>
            </endpoint-config>
            <client-config name="Standard-Client-Config"/>
        </subsystem>
        <subsystem xmlns="urn:jboss:domain:weld:4.0"/>
    </profile>
    <interfaces>
        <interface name="management">
            <inet-address value="${jboss.bind.address.management:127.0.0.1}"/>
        </interface>
        <interface name="public">
            <inet-address value="${jboss.bind.address:127.0.0.1}"/>
        </interface>
        <interface name="unsecure">
            <inet-address value="${jboss.bind.address.unsecure:127.0.0.1}"/>
        </interface>
    </interfaces>
    <socket-binding-group name="standard-sockets" default-interface="public" port-offset="${jboss.socket.binding.port-offset:0}">
        <socket-binding name="management-http" interface="management" port="${jboss.management.http.port:9990}"/>
        <socket-binding name="management-https" interface="management" port="${jboss.management.https.port:9993}"/>
        <socket-binding name="ajp" port="${jboss.ajp.port:8009}"/>
        <socket-binding name="http" port="${jboss.http.port:8080}"/>
        <socket-binding name="https" port="${jboss.https.port:8443}"/>
        <socket-binding name="iiop" interface="unsecure" port="3528"/>
        <socket-binding name="iiop-ssl" interface="unsecure" port="3529"/>
        <socket-binding name="txn-recovery-environment" port="4712"/>
        <socket-binding name="txn-status-manager" port="4713"/>
        <outbound-socket-binding name="mail-smtp">
            <remote-destination host="localhost" port="25"/>
        </outbound-socket-binding>
    </socket-binding-group>
</server>
/////////////////
package com.sat.serveb;

import javax.ejb.Remote;

@Remote
public interface DbBeanARemote {
		public String retConts();
		public String insPerson(int a,String b,String c);
		public String upPerson(int a,String b,String c);
		public String delPerson(int a);
}
/////
package com.sat.serveb;

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import javax.ejb.Stateful;
import javax.naming.InitialContext;
import javax.naming.NamingException;
import javax.sql.DataSource;

@Stateful
public class DbBeanA implements DbBeanARemote {
    public DbBeanA() {
    }

   
    
	@Override
	public String retConts() {
		String res="";
		try {
			 DataSource ds=(DataSource)(new InitialContext().lookup("java:jboss/MySqlDS"));
			Connection conn=ds.getConnection();
			Statement st=conn.createStatement();
			ResultSet rs=st.executeQuery("select * from persons");
			while(rs.next()) {
				res+=rs.getInt(1)+"-"+rs.getString(2)+"-"+rs.getString(3)+";";
			}
		} catch (NamingException e) {
			e.printStackTrace();
		} catch (SQLException e) {
			e.printStackTrace();
		}
		return res;
	}

	@Override
	public String insPerson(int a, String b, String c) {
		String status="Not Done";
		 try {
			DataSource ds=(DataSource)(new InitialContext().lookup("java:jboss/MySqlDS"));
			Connection conn=ds.getConnection();
			PreparedStatement ps=conn.prepareStatement("insert into persons values(?,?,?)");
			ps.setInt(1, a);
			ps.setString(2, b);
			ps.setString(3, c);
			ps.execute();
			status="Done";
		} catch (NamingException e) {
			e.printStackTrace();
		} catch (SQLException e) {
			e.printStackTrace();
		}
		return status;
	}

	@Override
	public String upPerson(int a, String b, String c) {
		String status="Not Done";
		 try {
			DataSource ds=(DataSource)(new InitialContext().lookup("java:jboss/MySqlDS"));
			Connection conn=ds.getConnection();
			PreparedStatement ps=conn.prepareStatement("update persons set name=?,dept=? where id=?");
			ps.setString(1, b);
			ps.setString(2, c);	
			ps.setInt(3, a);
			ps.executeUpdate();
			status="Done";
		} catch (NamingException e) {
			e.printStackTrace();
		} catch (SQLException e) {
			e.printStackTrace();
		}
		return status;
	}

	@Override
	public String delPerson(int a) {
		String status="Not Done";
		 try {
			DataSource ds=(DataSource)(new InitialContext().lookup("java:jboss/MySqlDS"));
			Connection conn=ds.getConnection();
			PreparedStatement ps=conn.prepareStatement("delete from persons where id=?");
			ps.setInt(1, a);
			ps.executeUpdate();
			status="Done";
		} catch (NamingException e) {
			e.printStackTrace();
		} catch (SQLException e) {
			e.printStackTrace();
		}
		return status;
	} 
}
/////
package co.sa.da.cli;

import java.util.Properties;
import java.util.Scanner;
import java.util.StringTokenizer;

import javax.naming.Context;
import javax.naming.InitialContext;
import javax.naming.NamingException;

import com.sat.serveb.DbBeanA;
import com.sat.serveb.DbBeanARemote;

public class MyClientCls {
	public static void main(String[] args) throws NamingException {
		DbBeanARemote dbr = EJBContext.retBean("ejb:");
		String res = dbr.retConts();
//		System.out.println(res);
		StringTokenizer str = new StringTokenizer(res, ";");
		while (str.hasMoreTokens()) {
			String u[] = str.nextToken().toString().split("-");
			for (String k : u) {
				System.out.println(k);
			}
			System.out.println("***********************");
			// System.out.println(str.nextToken().toString());
		}
		Scanner scan = new Scanner(System.in);
		System.out.println("Enter \n1 for insert\n2 for update\n3 for delete");
		int inp = Integer.parseInt(scan.nextLine());
		switch (inp) {
		case 1:
			System.out.println("Enter the id of the person");
			int a = Integer.parseInt(scan.nextLine());
			System.out.println("Enter name of the person");
			String b = scan.nextLine();
			System.out.println("Enter dept of the person");
			String c = scan.nextLine();
			dbr.insPerson(a, b, c);
			break;
		case 2:
			System.out.println("Enter the id of the person");
			int a1 = Integer.parseInt(scan.nextLine());
			System.out.println("Enter name of the person");
			String b1 = scan.nextLine();
			System.out.println("Enter dept of the person");
			String c1 = scan.nextLine();
			dbr.upPerson(a1, b1, c1);
			break;
		case 3:
			System.out.println("Enter the id of the person");
			int a2 = Integer.parseInt(scan.nextLine());
			dbr.delPerson(a2);
			break;
		default:
			System.out.println("Unsupported operation");
			break;
		}

	}

	private static class EJBContext {
		private static DbBeanARemote retBean(String namespace) throws NamingException {
			return retLookUp(namespace);
		}

		private static DbBeanARemote retLookUp(String namespace) throws NamingException {
			Context ctx = creaInitContext();
			String appName = "";
			String moduleName = "UnisysEighthProj";
			String distinctName = "";
			String beanName = DbBeanA.class.getSimpleName();
			String viewClassName = DbBeanARemote.class.getName();
			return (DbBeanARemote) ctx.lookup(namespace + appName + "/" + moduleName + "/" + distinctName + "/"
					+ beanName + "!" + viewClassName + "?stateful");
		}

		private static Context creaInitContext() throws NamingException {
			Properties props = new Properties();
			props.put(Context.INITIAL_CONTEXT_FACTORY, "org.jboss.naming.remote.client.InitialContextFactory");
			props.put(Context.URL_PKG_PREFIXES, "org.jboss.ejb.client.naming");
			props.put(Context.PROVIDER_URL, "http-remoting://localhost:8080");
			props.put("jboss.naming.client.ejb.context", true);
			return new InitialContext(props);
		}
	}

}
//////
package co.sa.da.cli;

import java.util.Properties;
import java.util.Scanner;
import java.util.StringTokenizer;

import javax.naming.Context;
import javax.naming.InitialContext;
import javax.naming.NamingException;

import com.sat.serveb.DbBeanA;
import com.sat.serveb.DbBeanARemote;

public class MyClientCls {
	public static void main(String[] args) throws NamingException {
		DbBeanARemote dbr = EJBContext.retBean("ejb:");
		selQuery(dbr);
		crudOpsMenu(dbr);
	}

	public static void selQuery(DbBeanARemote dbr) {
		String res = dbr.retConts();
		StringTokenizer str = new StringTokenizer(res, ";");
		while (str.hasMoreTokens()) {
			String u[] = str.nextToken().toString().split("-");
			for (String k : u) {
				System.out.println(k);
			}
			System.out.println("***********************");
		}
	}

	public static void crudOpsMenu(DbBeanARemote dbr) {
		Scanner scan = new Scanner(System.in);
		System.out.println("Enter \n1 for insert\n2 for update\n3 for delete");
		int inp = Integer.parseInt(scan.nextLine());
		switch (inp) {
		case 1:
			System.out.println("Enter the id of the person");
			int a = Integer.parseInt(scan.nextLine());
			System.out.println("Enter name of the person");
			String b = scan.nextLine();
			System.out.println("Enter dept of the person");
			String c = scan.nextLine();
			dbr.insPerson(a, b, c);
			break;
		case 2:
			System.out.println("Enter the id of the person");
			int a1 = Integer.parseInt(scan.nextLine());
			System.out.println("Enter name of the person");
			String b1 = scan.nextLine();
			System.out.println("Enter dept of the person");
			String c1 = scan.nextLine();
			dbr.upPerson(a1, b1, c1);
			break;
		case 3:
			System.out.println("Enter the id of the person");
			int a2 = Integer.parseInt(scan.nextLine());
			dbr.delPerson(a2);
			break;
		default:
			System.out.println("Unsupported operation");
			break;
		}
	}

	private static class EJBContext {
		private static DbBeanARemote retBean(String namespace) throws NamingException {
			return retLookUp(namespace);
		}

		private static DbBeanARemote retLookUp(String namespace) throws NamingException {
			Context ctx = creaInitContext();
			String appName = "";
			String moduleName = "UnisysEighthProj";
			String distinctName = "";
			String beanName = DbBeanA.class.getSimpleName();
			String viewClassName = DbBeanARemote.class.getName();
			return (DbBeanARemote) ctx.lookup(namespace + appName + "/" + moduleName + "/" + distinctName + "/"
					+ beanName + "!" + viewClassName + "?stateful");
		}

		private static Context creaInitContext() throws NamingException {
			Properties props = new Properties();
			props.put(Context.INITIAL_CONTEXT_FACTORY, "org.jboss.naming.remote.client.InitialContextFactory");
			props.put(Context.URL_PKG_PREFIXES, "org.jboss.ejb.client.naming");
			props.put(Context.PROVIDER_URL, "http-remoting://localhost:8080");
			props.put("jboss.naming.client.ejb.context", true);
			return new InitialContext(props);
		}
	}

}
/////
https://www.transfernow.net/dl/20240516joEW5m6Q/5JeCxhXI
////
create table bankaccount(acid int primary key,aname varchar(50), bname varchar(50), loc varchar(50));
/////
package com.satdb.ser;

import java.util.List;

import javax.ejb.Remote;

@Remote
public interface DbAccountBeanRemote {
		public List<String> retRecs();
		public String insAct(int a,String b,String c,String d);
		public String upAct(int a,String b,String c,String d);
		public String delAct(int a);
}

////

package com.satdb.ser;

import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import java.util.ArrayList;
import java.util.List;
import javax.ejb.Stateful;
import javax.naming.InitialContext;
import javax.naming.NamingException;
import javax.sql.DataSource;

@Stateful
public class DbAccountBean implements DbAccountBeanRemote {
	DataSource ds = null;
	Connection conn = null;

	public DbAccountBean() {
		try {
			ds = (DataSource) (new InitialContext().lookup("java:jboss/MySqlDS"));
			conn = ds.getConnection();
		} catch (NamingException e) {
			e.printStackTrace();
		} catch (SQLException e) {
			e.printStackTrace();
		}
	}

	@Override
	public List<String> retRecs() {
		List<String> ls = new ArrayList<String>();
		try {
			Statement st = conn.createStatement();
			ResultSet rs = st.executeQuery("select * from bankaccount");
			while (rs.next()) {
				ls.add(rs.getInt(1) + " " + rs.getString(2) + " " + rs.getString(3) + " " + rs.getString(4));
			}
		} catch (SQLException e) {
			e.printStackTrace();
		}
		return ls;
	}

	@Override
	public String insAct(int a, String b, String c, String d) {
		String status = "Not Done";
		try {
			PreparedStatement ps = conn
					.prepareStatement("insert into bankaccount values (" + a + ",'" + b + "','" + c + "','" + d + "')");
			ps.execute();
			status = "done";
		} catch (SQLException e) {
			e.printStackTrace();
		} finally {
			System.out.println(status);
		}
		return status;
	}

	@Override
	public String upAct(int a, String b, String c, String d) {
		String status = "Not Done";
		try {
			PreparedStatement ps = conn
					.prepareStatement("update bankaccount set aname='"+b+"',bname='"+c+"',loc='"+d+"' where acid="+a);
			ps.executeUpdate();
			status = "done";
			System.out.println(status);
		} catch (SQLException e) {
			e.printStackTrace();
		} finally {
			System.out.println(status);
		}
		return status;
	}

	@Override
	public String delAct(int a) {
		String status = "Not Done";
		try {
			PreparedStatement ps = conn
					.prepareStatement("delete from bankaccount where acid="+a);
			ps.executeUpdate();
			status = "done";
		} catch (SQLException e) {
			e.printStackTrace();
		} finally {
			System.out.println(status);
		}
		return status;
	}
}
/////

package com.satdb.cli;

import java.util.Properties;

import javax.naming.Context;
import javax.naming.InitialContext;
import javax.naming.NamingException;

import com.satdb.ser.DbAccountBean;
import com.satdb.ser.DbAccountBeanRemote;

public class MnClsClient {
	public static void main(String[] args) {
DbAccountBeanRemote dr=EJBContext.retBean("ejb:");
		System.out.println("Welcome to EJB table management systems for table bankaccount");
		System.out.println("What do you want to do today \n1 for select \n2 for insert \n3 for update \n4 for delete");
		Scanner scan=new Scanner(System.in);
		int ch=Integer.parseInt(scan.nextLine());
		if(ch==1) {
			List<String> ls=dr.retRecs();
			Iterator<String> itr=ls.iterator();
			while(itr.hasNext()) {
				System.out.println(itr.next());
			}
		}
		else if(ch==2) {
			System.out.println("Enter id of the account");
			int ac=Integer.parseInt(scan.nextLine());
			System.out.println("Enter name of the account holder");
			String an=scan.nextLine();
			System.out.println("Enter the name of the bank");
			String bn=scan.nextLine();
			System.out.println("Enter the loc");
			String loc=scan.nextLine();
			dr.insAct(ac, an, bn, loc);
		}
		else if(ch==3) {
			System.out.println("Enter id of the account");
			int ac=Integer.parseInt(scan.nextLine());
			System.out.println("Enter name of the account holder");
			String an=scan.nextLine();
			System.out.println("Enter the name of the bank");
			String bn=scan.nextLine();
			System.out.println("Enter the loc");
			String loc=scan.nextLine();
			dr.upAct(ac, an, bn, loc);
		}
		else if(ch==4) {
			System.out.println("Enter id of the account");
			int ac=Integer.parseInt(scan.nextLine());
			dr.delAct(ac);
		}
		else {
			System.out.println("Not a valid choice");
		}



		
	}
	
	private static class EJBContext{
		private static DbAccountBeanRemote retBean(String namespace) throws NamingException {
			return retLookUp(namespace);
		}

		private static DbAccountBeanRemote retLookUp(String namespace) throws NamingException {
			Context ctx = creaInitContext();
			String appName = "";
			String moduleName = "UnisysTenProj";
			String distinctName = "";
			String beanName = DbAccountBean.class.getSimpleName();
			String viewClassName = DbAccountBeanRemote.class.getName();
			return (DbAccountBeanRemote) ctx.lookup(namespace + appName + "/" + moduleName + "/" + distinctName + "/"
					+ beanName + "!" + viewClassName + "?stateful");
		}

		private static Context creaInitContext() throws NamingException {
			Properties props = new Properties();
			props.put(Context.INITIAL_CONTEXT_FACTORY, "org.jboss.naming.remote.client.InitialContextFactory");
			props.put(Context.URL_PKG_PREFIXES, "org.jboss.ejb.client.naming");
			props.put(Context.PROVIDER_URL, "http-remoting://localhost:8080");
			props.put("jboss.naming.client.ejb.context", true);
			return new InitialContext(props);
		}
	}
}
//////
package com.sat.timser;

import javax.annotation.Resource;
import javax.ejb.LocalBean;
import javax.ejb.SessionContext;
import javax.ejb.Stateless;
import javax.ejb.Timeout;
import javax.ejb.Timer;


@Stateless
public class MyTimer implements MyTimerRemote {
	@Resource
	private SessionContext sessContext;
    public MyTimer() {
    }

	@Override
	public void createTimerService(long duration) {
		System.out.println("Activating timer at "+System.currentTimeMillis());
		sessContext.getTimerService().createTimer(duration,"My Timer Started");
	}
	
	@Timeout
	public void handleTimeout(Timer t) {
		System.out.println("Time out fired at "+System.currentTimeMillis());
		t.cancel();
	}

}


/////
package com.sat.timser;

import javax.ejb.Remote;

@Remote
public interface MyTimerRemote {
	public void createTimerService(long duration);
}

/////
package com.sat.timserclient;

import java.util.Properties;

import javax.naming.Context;
import javax.naming.InitialContext;
import javax.naming.NamingException;

import com.sat.timser.MyTimer;
import com.sat.timser.MyTimerRemote;

public class ClientMain {

	public static void main(String[] args) throws NamingException {
		MyTimerRemote rem=EJBContext.retBean("ejb:");
		rem.createTimerService(5000);
		
	}
	
	private static class EJBContext{
		private static MyTimerRemote retBean(String namespace) throws NamingException {
			return retLookUp(namespace);
		}

		private static MyTimerRemote retLookUp(String namespace) throws NamingException {
			Context ctx = creaInitContext();
			String appName = "";
			String moduleName = "UnisysElevenProj";
			String distinctName = "";
			String beanName = MyTimer.class.getSimpleName();
			String viewClassName = MyTimerRemote.class.getName();
			return (MyTimerRemote) ctx.lookup(namespace + appName + "/" + moduleName + "/" + distinctName + "/"
					+ beanName + "!" + viewClassName);
		}

		private static Context creaInitContext() throws NamingException {
			Properties props = new Properties();
			props.put(Context.INITIAL_CONTEXT_FACTORY, "org.jboss.naming.remote.client.InitialContextFactory");
			props.put(Context.URL_PKG_PREFIXES, "org.jboss.ejb.client.naming");
			props.put(Context.PROVIDER_URL, "http-remoting://localhost:8080");
			props.put("jboss.naming.client.ejb.context", true);
			return new InitialContext(props);
		}
	}
	}


//////
package com.satejb.timser;

import javax.ejb.Remote;

@Remote
public interface ATimerRemote {
	public void createATimer(long duration);
}

/////
package com.satejb.timser;

import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;
import java.util.Date;

import javax.annotation.Resource;
import javax.ejb.LocalBean;
import javax.ejb.SessionContext;
import javax.ejb.Stateless;
import javax.ejb.Timeout;
import javax.ejb.Timer;

/**
 * Session Bean implementation class ATimer
 */
@Stateless
@LocalBean
public class ATimer implements ATimerRemote {

   @Resource
   private SessionContext sessContext;
	
	
	
    public ATimer() {
    }
    

	@Override
	public void createATimer(long duration) {
		sessContext.getTimerService().createTimer(duration, "ATimer");
	}
	
	@Timeout
	public void handleTimeout(Timer timer ) {
		System.out.println("Time out fired");
		Date dt=new Date();
		String jj=dt.getHours()+":"+dt.getMinutes()+":"+dt.getSeconds();
		jj+="Our scheduled timer fired after so many millis";
		FileOutputStream fos;
		String k="unisyslog"+dt.getTime();
		try {
			fos = new FileOutputStream(new File("C:\\delhiofficefiles\\"+k));
			fos.write(jj.getBytes());
			fos.flush();
			fos.close();
		} catch (FileNotFoundException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		
		timer.cancel();
	}


	@Override
	public void timMeth() {
		System.out.println("Method fired after a minute");
	}

}
/////
package com.satejb.timser;

import javax.ejb.Remote;
import javax.ejb.Schedule;

@Remote
public interface ATimerRemote {
	public void createATimer(long duration);
	@Schedule(minute  = "1")
	public void timMeth();
}
////
package com.satejb.timser.cli;

import java.util.Properties;

import javax.naming.Context;
import javax.naming.InitialContext;
import javax.naming.NamingException;
import com.satejb.timser.ATimer;
import com.satejb.timser.ATimerRemote;

public class MnClsClient {

	public static void main(String[] args) throws NamingException {
			ATimerRemote at=EJBContext.retBean("ejb:");
			at.createATimer(5000);
			at.timMeth();
	}

	private static class EJBContext{
		private static ATimerRemote retBean(String namespace) throws NamingException {
			return retLookUp(namespace);
		}

		private static ATimerRemote retLookUp(String namespace) throws NamingException {
			Context ctx = creaInitContext();
			String appName = "";
			String moduleName = "UnisysTwelveProj";
			String distinctName = "";
			String beanName = ATimer.class.getSimpleName();
			String viewClassName = ATimerRemote.class.getName();
			return (ATimerRemote) ctx.lookup(namespace + appName + "/" + moduleName + "/" + distinctName + "/"
					+ beanName + "!" + viewClassName);
		}

		private static Context creaInitContext() throws NamingException {
			Properties props = new Properties();
			props.put(Context.INITIAL_CONTEXT_FACTORY, "org.jboss.naming.remote.client.InitialContextFactory");
			props.put(Context.URL_PKG_PREFIXES, "org.jboss.ejb.client.naming");
			props.put(Context.PROVIDER_URL, "http-remoting://localhost:8080");
			props.put("jboss.naming.client.ejb.context", true);
			return new InitialContext(props);
		}
	}
}

/////
package com.satejb.timser;

import java.io.File;
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.SQLException;
import java.util.Date;

import javax.annotation.Resource;
import javax.ejb.LocalBean;
import javax.ejb.SessionContext;
import javax.ejb.Stateless;
import javax.ejb.Timeout;
import javax.ejb.Timer;
import javax.naming.InitialContext;
import javax.naming.NamingException;
import javax.sql.DataSource;

/**
 * Session Bean implementation class ATimer
 */
@Stateless
@LocalBean
public class ATimer implements ATimerRemote {

   @Resource
   private SessionContext sessContext;
	
	
	
    public ATimer() {
    }
    

	@Override
	public void createATimer(long duration) {
		sessContext.getTimerService().createTimer(duration, "ATimer");
	}
	
	@Timeout
	public void handleTimeout(Timer timer ) {
		System.out.println("Time out fired");
		Date dt=new Date();
		String jj=dt.getHours()+":"+dt.getMinutes()+":"+dt.getSeconds();
		jj+="Our scheduled timer fired after so many millis";
		FileOutputStream fos;
		String k="unisyslog"+dt.getTime();
		try {
			fos = new FileOutputStream(new File("C:\\delhiofficefiles\\"+k));
			fos.write(jj.getBytes());
			fos.flush();
			fos.close();
		} catch (FileNotFoundException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		
		timer.cancel();
	}

	

	@Override
	public void timMeth(int aa,String b,String c,String d) {
		DataSource ds;
		try {
			ds = (DataSource)(new InitialContext().lookup("java:jboss/MySqlDS"));
			Connection conn=ds.getConnection();
			String query="insert into bankaccount values("+aa+",'"+b+"','"+c+"','"+d+"')";
			PreparedStatement ps=conn.prepareStatement(query);
			ps.execute();
		} catch (NamingException e) {
			e.printStackTrace();
		} catch (SQLException e) {
			e.printStackTrace();
		}
		
		
		
		
//		System.out.println("Method fired after a minute");
	}

}
/////
package com.satejb.timser;

import javax.ejb.Remote;
import javax.ejb.Schedule;

@Remote
public interface ATimerRemote {
	public void createATimer(long duration);
	@Schedule(second =    "10")
	public void timMeth(int aa,String b,String c,String d);
}
////
ATimerRemote at=EJBContext.retBean("ejb:");
			at.createATimer(5000);
//			at.timMeth();
			at.timMeth( 12, "zuakowski", "Bank Of Maryland","Washington");
////////
Persistence.xml
<?xml version="1.0" encoding="UTF-8"?>
<persistence version="2.0"
   xmlns="http://java.sun.com/xml/ns/persistence" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
   xsi:schemaLocation="
        http://java.sun.com/xml/ns/persistence
        http://java.sun.com/xml/ns/persistence/persistence_2_0.xsd">
   <persistence-unit name="primary">
      <jta-data-source>java:jboss/MySqlDS</jta-data-source>
      <properties>
         <!-- Properties for Hibernate -->
         <property name="hibernate.hbm2ddl.auto" value="update" />
         <!-- Print's out the SQL statement Hibernate is using to the console, useful for debugging -->
         <property name="hibernate.show_sql" value="true" />
      </properties>
   </persistence-unit>
</persistence>
/////

package com.sat.mods;

import javax.persistence.Entity;
import javax.persistence.Id;
import javax.persistence.Table;

@Entity
@Table(name = "bankaccount")
public class BankAccount  implements Serializable{
	private int acid;
	@Id
	public int getAcid() {
		return acid;
	}
	public void setAcid(int acid) {
		this.acid = acid;
	}
	public String getAname() {
		return aname;
	}
	public void setAname(String aname) {
		this.aname = aname;
	}
	public String getBname() {
		return bname;
	}
	public void setBname(String bname) {
		this.bname = bname;
	}
	public String getLoc() {
		return loc;
	}
	public void setLoc(String loc) {
		this.loc = loc;
	}
	private String aname;
	private String bname;
	private String loc;
}
/////

package com.sat.cls;

import java.util.List;

import javax.ejb.Remote;

import com.sat.mods.BankAccount;

@Remote
public interface BankAccountPersistentBeanRemote {
		public List<BankAccount> retList();
}
/////
package com.sat.cls;

import java.util.List;

import javax.ejb.LocalBean;
import javax.ejb.Remote;
import javax.ejb.Stateless;
import javax.persistence.EntityManager;
import javax.persistence.PersistenceContext;

import com.sat.mods.BankAccount;


@Stateless
@Remote
public class BankAccountPersistentBean implements BankAccountPersistentBeanRemote {
  
    public BankAccountPersistentBean() {
    }

    @PersistenceContext(name = "primary")
    private EntityManager entityManager; 
    
	@Override
	public List<BankAccount> retList() {
		List<BankAccount> lb=null;
		lb=(List<BankAccount>)entityManager.createQuery("From BankAccount").getResultList();
		return lb;
	}

}
////
package c.b.a;

import java.util.List;
import java.util.Properties;

import javax.naming.Context;
import javax.naming.InitialContext;
import javax.naming.NamingException;

import com.sat.cls.BankAccountPersistentBean;
import com.sat.cls.BankAccountPersistentBeanRemote;
import com.sat.mods.BankAccount;

public class MnClsClient {

	public static void main(String[] args) throws NamingException {
		BankAccountPersistentBeanRemote br=EJBContext.retBean("ejb:");
		List<BankAccount> lb=br.retList();
		for(BankAccount b:lb) {
			System.out.println(b.getAcid()+" "+b.getAname()+" "+b.getBname()+" "+b.getLoc());
		}
	}

	private static class EJBContext{
		private static BankAccountPersistentBeanRemote retBean(String namespace) throws NamingException {
			return retLookUp(namespace);
		}

		private static BankAccountPersistentBeanRemote retLookUp(String namespace) throws NamingException {
			Context ctx = creaInitContext();
			String appName = "";
			String moduleName = "UnisysThirteenProj";
			String distinctName = "";
			String beanName = BankAccountPersistentBean.class.getSimpleName();
			String viewClassName = BankAccountPersistentBeanRemote.class.getName();
			return (BankAccountPersistentBeanRemote) ctx.lookup(namespace + appName + "/" + moduleName + "/" + distinctName + "/"
					+ beanName + "!" + viewClassName);
		}

		private static Context creaInitContext() throws NamingException {
			Properties props = new Properties();
			props.put(Context.INITIAL_CONTEXT_FACTORY, "org.jboss.naming.remote.client.InitialContextFactory");
			props.put(Context.URL_PKG_PREFIXES, "org.jboss.ejb.client.naming");
			props.put(Context.PROVIDER_URL, "http-remoting://localhost:8080");
			props.put("jboss.naming.client.ejb.context", true);
			return new InitialContext(props);
		}
	}
	
	
}
////
	public void addAccount(BankAccount b);
	public void upAccount(BankAccount b);
	public void delAccount(BankAccount b);
////
package c.b.a;

import java.util.List;
import java.util.Properties;

import javax.naming.Context;
import javax.naming.InitialContext;
import javax.naming.NamingException;

import com.sat.cls.BankAccountPersistentBean;
import com.sat.cls.BankAccountPersistentBeanRemote;
import com.sat.mods.BankAccount;

public class MnClsClient {

	public static void main(String[] args) throws NamingException {
		BankAccountPersistentBeanRemote br=EJBContext.retBean("ejb:");
		int a=13;
		String b="Melinda Tsariski";
		String c="Royal Bank  Of Ireland";
		String d="new street, Dublin";
		BankAccount ba=new BankAccount();
		ba.setAcid(a);
		ba.setAname(b);
		ba.setBname(c);
		ba.setLoc(d);
//		br.addAccount(ba);
//		br.upAccount(ba);
		br.delAccount(ba);
	}

	public static void selMeth(BankAccountPersistentBeanRemote br) {
		List<BankAccount> lb=br.retList();
		for(BankAccount b:lb) {
			System.out.println(b.getAcid()+" "+b.getAname()+" "+b.getBname()+" "+b.getLoc());
		}
	}

	private static class EJBContext{
		private static BankAccountPersistentBeanRemote retBean(String namespace) throws NamingException {
			return retLookUp(namespace);
		}

		private static BankAccountPersistentBeanRemote retLookUp(String namespace) throws NamingException {
			Context ctx = creaInitContext();
			String appName = "";
			String moduleName = "UnisysThirteenProj";
			String distinctName = "";
			String beanName = BankAccountPersistentBean.class.getSimpleName();
			String viewClassName = BankAccountPersistentBeanRemote.class.getName();
			return (BankAccountPersistentBeanRemote) ctx.lookup(namespace + appName + "/" + moduleName + "/" + distinctName + "/"
					+ beanName + "!" + viewClassName);
		}

		private static Context creaInitContext() throws NamingException {
			Properties props = new Properties();
			props.put(Context.INITIAL_CONTEXT_FACTORY, "org.jboss.naming.remote.client.InitialContextFactory");
			props.put(Context.URL_PKG_PREFIXES, "org.jboss.ejb.client.naming");
			props.put(Context.PROVIDER_URL, "http-remoting://localhost:8080");
			props.put("jboss.naming.client.ejb.context", true);
			return new InitialContext(props);
		}
	}
	
	
}
//////
package com.sat.cls;

import java.util.List;

import javax.ejb.LocalBean;
import javax.ejb.Remote;
import javax.ejb.Stateless;
import javax.persistence.EntityManager;
import javax.persistence.PersistenceContext;

import com.sat.mods.BankAccount;


@Stateless
@Remote
public class BankAccountPersistentBean implements BankAccountPersistentBeanRemote {
  
    public BankAccountPersistentBean() {
    }

    @PersistenceContext(name = "primary")
    private EntityManager entityManager; 
    
	@Override
	public List<BankAccount> retList() {
		List<BankAccount> lb=null;
		lb=(List<BankAccount>)entityManager.createQuery("From BankAccount").getResultList();
		return lb;
	}

	@Override
	public void addAccount(BankAccount b) {
		entityManager.persist(b);
	}

	@Override
	public void upAccount(BankAccount b) {
		entityManager.merge(b);
	}

	@Override
	public void delAccount(BankAccount b) {
		BankAccount ba=entityManager.find(BankAccount.class, b.getAcid());
		entityManager.remove(ba);
	}
}
/////
