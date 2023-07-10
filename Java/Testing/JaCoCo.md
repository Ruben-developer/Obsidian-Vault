Para usar test de cobertura en Java, necesitarás una herramienta de análisis de cobertura de código como JaCoCo o Cobertura. Estas herramientas se integran con tu entorno de desarrollo y te permiten ejecutar tus pruebas unitarias y generar informes que muestran qué parte de tu código ha sido cubierta por las pruebas.

Puedes configurar JaCoCo o Cobertura en tu proyecto a través de tu archivo pom.xml. Una vez configurado, puedes ejecutar tus pruebas unitarias y generar informes de cobertura de código que muestren qué líneas de código han sido cubiertas por las pruebas y cuáles no.

Por ejemplo, para configurar JaCoCo en tu proyecto, necesitas agregar las siguientes líneas a tu archivo pom.xml:

```xml
<build>
	<plugins>
		<plugin>
			<groupId>org.jacoco</groupId>
			<artifactId>jacoco-maven-plugin</artifactId>
			<version>0.8.7</version>
			<executions>
				<execution>
					<goals>
						<goal>prepare-agent</goal>
					</goals>
				</execution>
				<execution>
					<id>report</id>
					<phase>test</phase>
						<goals>
							<goal>report</goal>
						</goals>
				</execution>
			</executions>
		</plugin>
		...
	</plugins>
</build>
```

Una vez que hayas agregado esto a tu archivo pom.xml, puedes ejecutar tus pruebas unitarias y generar informes de cobertura de código con el siguiente comando en la línea de comandos:

```cpp
mvn test
```

Esto ejecutará todas tus pruebas unitarias y generará un informe de cobertura de código que puedes ver en tu navegador web.