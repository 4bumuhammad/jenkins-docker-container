# Jenkins : with Docker Container

&nbsp;

**Reference repository registry image :**<br />
- jenkins/jenkins
    <pre>https://hub.docker.com/r/jenkins/jenkins/tags</pre>

&nbsp;

### Command Docker Container:

    ❯ docker run -d \
        --name jenkins-container \
        -p 8080:8080 -p 50000:50000 \
        -v /Users/powercommerce/Documents/test/docker-mount/jenkins_home:/var/jenkins_home \
        jenkins/jenkins:jdk21

<pre>
        Unable to find image 'jenkins/jenkins:jdk21' locally
        jdk21: Pulling from jenkins/jenkins
        1e92f3a395ff: Pull complete 
        67fe5d2b015b: Pull complete 
        213daba12592: Pull complete 
        307d99bcf277: Pull complete 
        0896aa74386f: Pull complete 
        c31b56b91c1e: Pull complete 
        d8178c7a3240: Pull complete 
        ab454a4fedc9: Pull complete 
        c13b5f3c853a: Pull complete 
        df35beb7e844: Pull complete 
        2229b8b635a7: Pull complete 
        5902a951fefe: Pull complete 
        Digest: sha256:5d98ba5505a22b17393dfc6c471d3af540bcc72268d3f89adfa9cf0a9f2b9bf0
        Status: Downloaded newer image for jenkins/jenkins:jdk21
        c42df08a060f11e51ed23802f75c77ba30388c553ef01fe5104bc3b7db04b002
</pre>

&nbsp;

<pre>
    ❯ docker images

        REPOSITORY        TAG       IMAGE ID       CREATED      SIZE
        jenkins/jenkins   jdk21     b2212b3b5405   2 days ago   510MB


    ❯ docker ps -a 

        CONTAINER ID   IMAGE                   COMMAND                  CREATED         STATUS         PORTS                                              NAMES
        c42df08a060f   jenkins/jenkins:jdk21   "/usr/bin/tini -- /u…"   8 minutes ago   Up 8 minutes   0.0.0.0:8080->8080/tcp, 0.0.0.0:50000->50000/tcp   jenkins-container</pre>
</pre>

&nbsp;

**Docker Logs :**
<pre>
    ❯ docker logs jenkins-container

        Running from: /usr/share/jenkins/jenkins.war
        webroot: /var/jenkins_home/war
        2024-04-19 00:52:09.255+0000 [id=1]     INFO    winstone.Logger#logInternal: Beginning extraction from war file
        2024-04-19 00:52:31.251+0000 [id=1]     WARNING o.e.j.s.handler.ContextHandler#setContextPath: Empty contextPath
        2024-04-19 00:52:31.294+0000 [id=1]     INFO    org.eclipse.jetty.server.Server#doStart: jetty-10.0.20; built: 2024-01-29T20:46:45.278Z; git: 3a745c71c23682146f262b99f4ddc4c1bc41630c; jvm 21.0.2+13-LTS
        2024-04-19 00:52:32.104+0000 [id=1]     INFO    o.e.j.w.StandardDescriptorProcessor#visitServlet: NO JSP Support for /, did not find org.eclipse.jetty.jsp.JettyJspServlet
        2024-04-19 00:52:32.201+0000 [id=1]     INFO    o.e.j.s.s.DefaultSessionIdManager#doStart: Session workerName=node0
        2024-04-19 00:52:33.671+0000 [id=1]     INFO    hudson.WebAppMain#contextInitialized: Jenkins home directory: /var/jenkins_home found at: EnvVars.masterEnvVars.get("JENKINS_HOME")
        2024-04-19 00:52:34.074+0000 [id=1]     INFO    o.e.j.s.handler.ContextHandler#doStart: Started w.@4cb40e3b{Jenkins v2.454,/,file:///var/jenkins_home/war/,AVAILABLE}{/var/jenkins_home/war}
        2024-04-19 00:52:34.079+0000 [id=1]     INFO    o.e.j.server.AbstractConnector#doStart: Started ServerConnector@bf1ec20{HTTP/1.1, (http/1.1)}{0.0.0.0:8080}
        2024-04-19 00:52:34.085+0000 [id=1]     INFO    org.eclipse.jetty.server.Server#doStart: Started Server@3eeb318f{STARTING}[10.0.20,sto=0] @25279ms
        2024-04-19 00:52:34.086+0000 [id=33]    INFO    winstone.Logger#logInternal: Winstone Servlet Engine running: controlPort=disabled
        2024-04-19 00:52:35.136+0000 [id=41]    INFO    jenkins.InitReactorRunner$1#onAttained: Started initialization
        2024-04-19 00:52:35.246+0000 [id=43]    INFO    jenkins.InitReactorRunner$1#onAttained: Listed all plugins
        2024-04-19 00:52:37.906+0000 [id=40]    INFO    jenkins.InitReactorRunner$1#onAttained: Prepared all plugins
        2024-04-19 00:52:37.921+0000 [id=39]    INFO    jenkins.InitReactorRunner$1#onAttained: Started all plugins
        2024-04-19 00:52:37.954+0000 [id=43]    INFO    jenkins.InitReactorRunner$1#onAttained: Augmented all extensions
        2024-04-19 00:52:38.630+0000 [id=40]    INFO    jenkins.InitReactorRunner$1#onAttained: System config loaded
        2024-04-19 00:52:38.631+0000 [id=42]    INFO    jenkins.InitReactorRunner$1#onAttained: System config adapted
        2024-04-19 00:52:38.631+0000 [id=42]    INFO    jenkins.InitReactorRunner$1#onAttained: Loaded all jobs
        2024-04-19 00:52:38.632+0000 [id=42]    INFO    jenkins.InitReactorRunner$1#onAttained: Configuration for all jobs updated
        2024-04-19 00:52:38.718+0000 [id=57]    INFO    hudson.util.Retrier#start: Attempt #1 to do the action check updates server
        2024-04-19 00:52:39.799+0000 [id=39]    INFO    jenkins.install.SetupWizard#init: 

        *************************************************************
        *************************************************************
        *************************************************************

        Jenkins initial setup is required. An admin user has been created and a password generated.
        Please use the following password to proceed to installation:

        bba767aa51f14ccaa1147d6bd1591c9c

        This may also be found at: /var/jenkins_home/secrets/initialAdminPassword

        *************************************************************
        *************************************************************
        *************************************************************

        2024-04-19 00:52:49.590+0000 [id=57]    INFO    h.m.DownloadService$Downloadable#load: Obtained the updated data file for hudson.tasks.Maven.MavenInstaller
        2024-04-19 00:52:49.592+0000 [id=57]    INFO    hudson.util.Retrier#start: Performed the action check updates server successfully at the attempt #1
        2024-04-19 00:52:56.795+0000 [id=44]    INFO    jenkins.InitReactorRunner$1#onAttained: Completed initialization
        2024-04-19 00:52:56.853+0000 [id=32]    INFO    hudson.lifecycle.Lifecycle#onReady: Jenkins is fully up and running

</pre>

&nbsp;

---

&nbsp;

&nbsp;

&nbsp;

<div align="center">
    <img src="./gambar-petunjuk/well_done.png" alt="well_done" style="display: block; margin: 0 auto;">
</div> 

&nbsp;

---

&nbsp;

&nbsp;

&nbsp;
