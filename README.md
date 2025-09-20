import jakarta.servlet.ServletException;
import jakarta.servlet.annotation.WebServlet;
import jakarta.servlet.http.*;

import java.io.IOException;
import java.io.PrintWriter;
import java.net.URLDecoder;
import java.net.URLEncoder;
import java.nio.charset.StandardCharsets;

@WebServlet("/welcome")
public class WelcomeServlet extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        HttpSession session=req.getSession(false);//do not create session obj if already there

        String name=(session!=null)?(String) session.getAttribute("userName"):"Guest";
        String email=(session!=null)?(String) session.getAttribute("userEmail"):"Not Available";

        Cookie[] cookies= req.getCookies();
        String cookieUser="Guest";

        if(cookies!=null){
            for(Cookie c:cookies){
               if(c.getName().equalsIgnoreCase("user")){
                   URLDecoder.decode(c.getValue(), StandardCharsets.UTF_8.toString());
               }
            }

        }

        resp.setContentType("text/html");
        PrintWriter out=resp.getWriter();
        out.println("<h2>Welcome Buddy "+name+"</h2>");
        out.println("<h2>Your Email "+email+"</h2>");

    }
}
