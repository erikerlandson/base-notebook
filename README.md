
### Build beaker-x container and run it

At the time of this doc, the [BeakerX project](https://github.com/twosigma/beakerx) is about 15 days old, and has no releases.
So I'm saving this, and can revisit when they issue some kind of release.

Will likely have to update the build logic on `Dockerfile-beakerx` to get
it synced with the project.

I never tested how to get the scala kernel to see the spark install.  TBD.

```bash
% docker build -f Dockerfile -t beakerx-base-nb:latest .
% docker build -f Dockerfile-beakerx -t manyangled/beaker-nb:latest .
% docker push manyangled/beaker-nb:latest
% oc run beaker-nb --image=manyangled/beaker-nb:latest --expose --port=8888
```

Expose a route to the `beaker-nb` service, then hit the route from your browser.
It should bring up a notebook interface where you can start creating
notebooks.
