# 3.1-23bcs12579
User Login Using Servlet and HTML Form

import java.io.IOException;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import javax.servlet.http.HttpSession;

@WebServlet("/loginServlet")
public class LoginServlet extends HttpServlet {
    private static final long serialVersionUID = 1L;

    protected void doPost(HttpServletRequest request, HttpServletResponse response)
        throws ServletException, IOException {

        String emailId = request.getParameter("emailId");
        String password = request.getParameter("password");

        // Demo authentication (replace this with database connection for real use)
        if (emailId != null && emailId.equalsIgnoreCase("admin@gmail.com")
                && password != null && password.equalsIgnoreCase("admin")) {
            HttpSession session = request.getSession();
            session.setAttribute("emailId", emailId);
            response.sendRedirect("welcome.jsp");
        } else {
            response.getWriter().println("Login failed. Invalid credentials.");
        }
    }
}



