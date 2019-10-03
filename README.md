# lein-gcs-wagon

Deploy and consume artifacts in Google Cloud Storage (GCS) repositories in 
[Leiningen](https://github.com/technomancy/leiningen) projects.

A minimal wrapper around [maven-wagon-gs](https://github.com/janhicken/maven-wagon-gs).

## Usage

The plugin uses Google [Application Default Credentials](https://cloud.google.com/docs/authentication/production) for
authentication. These are available automatically in e.g. Compute Engine VMs and Kubernetes Pods. You can set the
credentials in your local environment with an environment variable:

```bash
export GOOGLE_APPLICATION_CREDENTIALS="/path/to/my/credentials.json"
```

Create the GCS bucket you are going to use and add the configuration in your application's project.clj:
```clojure
:repositories [["snapshots" {:url           "gs://my-bucket/snapshots"
                             :no-auth       true
                             :sign-releases false}]
               ["releases" {:url           "gs://my-bucket/releases"
                            :no-auth       true
                            :sign-releases false}]]
:plugins [[lupapiste/lein-gcs-wagon "1.1"]]
```

See [Leiningen documentation](https://github.com/technomancy/leiningen/blob/master/doc/DEPLOY.md) for more information
about repository configuration.

## License

Based on [maven-wagon-gs](https://github.com/janhicken/maven-wagon-gs) by Jan Hicken and other contributors.

Distributed under the Apache License 2.0.
