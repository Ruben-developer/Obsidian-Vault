Este ejemplo de código usa la biblioteca "io.jsonwebtoken" para generar y verificar tokens JWT. El método "generateJWT" toma como entrada un sujeto, un tiempo de vida en milisegundos y una clave secreta, y devuelve un token JWT. El método "verifyJWT" toma como entrada un token JWT y una clave secreta, y devuelve verdadero si el token es válido y falso de lo contrario.

```java
// Importar las bibliotecas necesarias
import io.jsonwebtoken.Claims;
import io.jsonwebtoken.Jwts;
import io.jsonwebtoken.SignatureAlgorithm;
import java.util.Date;

// Crear una clase pública que genere un token JWT
public class JWTGenerator {
	
	// Método que genera un token JWT
	public String generateJWT(String subject, long ttlMillis, String key) {
		
	    // Definir la fecha actual y la fecha de expiración
	    long nowMillis = System.currentTimeMillis();
	    Date now = new Date(nowMillis);
	    Date exp = new Date(nowMillis + ttlMillis);
	    
	    // Crear el token JWT
	    String jwt = Jwts.builder()
	        .setSubject(subject)
	        .setIssuedAt(now)
	        .setExpiration(exp)
	        .signWith(SignatureAlgorithm.HS256, key)
	        .compact();
	    return jwt;
	}
	
	// Método que verifica que el token JWT sea válido
	public boolean verifyJWT(String jwt, String key) {
	    try {
			  Claims claims = Jwts.parser().setSigningKey(key).parseClaimsJws(jwt).getBody();
		    return true;
	    } catch (Exception e) {
		    return false;
	    }
	}
}
```
