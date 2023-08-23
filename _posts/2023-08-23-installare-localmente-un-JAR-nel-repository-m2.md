---
layout: post
title: Installare localmente un JAR sul repository .m2
subtitle: Rendere disponibile una dipendenza in locale senza attingere da Maven Central
#cover-img: /assets/img/path.jpg
#thumbnail-img: /assets/img/thumb.png
#share-img: /assets/img/path.jpg
tags: [Java, Maven]
---

In uno degl'ultimi progetti sviluppati un intera sezione del progetto poteva essere molto utile ad altri colleghi per risolvere le stesse problematiche. Rendendolo un progetto separato e essendo ancora pubblicato su Maven Central, la necessità di integrare il codice all'interno del progetto principale si è resa evidente. 

Per questo una volta creato il JAR con le dipendenze è possibile installare localmente la dipendeza per poi poterla recuperare come di consueto tramite il pom.xml del progetto.

Procediamo come segue:
- Impostare il progetto in modo tale da generare il JAR con le dipendenze

```
<dependencies>
  <dependency>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-assembly-plugin</artifactId>
        <version>3.4.2</version>
        <type>maven-plugin</type>
    </dependency>
</dependencies>

<build>
  <plugins>
    <plugin>
      <groupId>org.apache.maven.plugins</groupId>
      <artifactId>maven-assembly-plugin</artifactId>
      <configuration>
          <descriptorRefs>
              <descriptorRef>jar-with-dependencies</descriptorRef>
          </descriptorRefs>
          <archive>
              <manifest>
                <mainClass>it.gbale.apisports.ApiSports</mainClass>
              </manifest>
          </archive>
      </configuration>
      <executions>
          <execution>
              <id>make-assembly</id>
              <phase>package</phase>
              <goals>
                <goal>single</goal>
              </goals>
          </execution>
      </executions>
    </plugin>
  </plugins>
</build>
```

- Generare il JAR

```
mvn clean package
```

- Installare localmente un JAR sul repository .m2 

```
// Se il progetto aveva il pom.xml

mvn install:install-file \
-Dfile=target/api-football-wrapper-1.1-SNAPSHOT.jar \
-DpomFile=pom.xml

// Se il progetto non aveva il pom.xml

mvn install:install-file \
-Dfile=target/api-football-wrapper-1.1-SNAPSHOT.jar \
-DgroupId=it.gbale.apisports \
-DartifactId=api-football-wrapper \
-Dversion=1.0-SNAPSHOT \
-Dpackaging=jar

//Se si vuole associare anche il codice sorgente

-Dsources=target/restmud-engine-1.4-SNAPSHOT-sources.jar
```

Una volta fatto ciò sarà possibile inserire la dipendenza all'interno del pom.xml del tuo progetto.
