<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Meu Site</title>
</head>
<body>
    <h1>Bem-vindo ao Meu Site!</h1>
    <form action="processa" method="post">
        <label for="nome">Digite seu nome:</label>
        <input type="text" id="nome" name="nome" required>
        <input type="submit" value="Enviar">
    </form>
</body>
import java.io.IOException;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

@WebServlet("/processa")
public class ProcessaServlet extends HttpServlet {
    private static final long serialVersionUID = 1L;

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) 
            throws ServletException, IOException {
        // Obtém o parâmetro do formulário
        String nome = request.getParameter("nome");
        
        // Define o tipo de resposta
        response.setContentType("text/html");
        
        // Escreve a resposta
        response.getWriter().println("<html><body>");
        response.getWriter().println("<h1>Olá, " + nome + "!</h1>");
        response.getWriter().println("</body></html>");
    }
}
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee
                             http://xmlns.jcp.org/xml/ns/javaee/web-app_3_1.xsd"
         version="3.1">
    <servlet>
        <servlet-name>ProcessaServlet</servlet-name>
        <servlet-class>com.example.ProcessaServlet</servlet-class>
    </servlet>
    <servlet-mapping>
        <servlet-name>ProcessaServlet</servlet-name>
        <url-pattern>/processa</url-pattern>
    </servlet-mapping>
</web-app>
