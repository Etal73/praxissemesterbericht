````
<filters>  
    <filter>       
     <artifactSet>        
         <includes>               
          <include>com.fasterxml.jackson.annotation</include>  
            <include>com.fasterxml.jackson.databind</include>  
        </includes>            
        <excludes>                
	        <exclude>META-INF/LICENSE</exclude>  
		</excludes>        
	</artifactSet>        
	<artifactSet>            
		<includes>                
			<include>org.java_websocket</include>  
            <incldue>com.fasterxml.jackson.core</incldue>  
            <include>com.fasterxml.jackson.databind</include>  
            <include>org.slf4j</include>  
        </includes>            
        <excludes>                
	        <exclude>META-INF.versions.9.module-info</exclude>  
        </excludes>        
    </artifactSet>        
    <artifactSet>            
        <includes>                
	        <include>org.java_websocket</include>  
            <include>com.fasterxml.jackson.annotation</include>  
            <include>com.fasterxml.jackson.core</include>  
            <include>com.fasterxml.jackson.databind</include>  
            <include>org.slf4j</include>  
        </includes>           
        <excludes>                
            <exclude>META-INF/MANIFEST.MF</exclude>  
        </excludes>        
    </artifactSet>    
    </filter>
</filters>


<artifactSet>  
    <includes>        
	    <include>:</include>  
    </includes>    
    <excludes>        
	    <exclude>module-info.java</exclude>  
    </excludes>
</artifactSet>



<plugin>  
    <groupId>org.apache.maven.plugins</groupId>  
    <artifactId>maven-shade-plugin</artifactId>  
    <version>3.5.0</version>  
    <executions>        
    <execution>            
    <phase>package</phase>  
            <goals><goal>shade</goal></goals>  
        </execution>    
        </executions>    
        <configuration>        <createDependencyReducedPom>false</createDependencyReducedPom>  
        <transformers>            
        <transformer implementation = "org.apache.maven.plugins.shade.resource.ManifestResourceTransformer">  
                <manifestEntries>                    
                <Main-Class>de.howatherm.SDplugin.MAIN</Main-Class>  
                </manifestEntries>           
                 </transformer>        
                 </transformers>    
                 </configuration>
                 </plugin>














```
