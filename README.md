pf2rpm
------

pf2rpm, short for puppet forge to rpm, is a tool designed to ease
integration between open source puppet modules and rpm based systems.  It
serves this end by providing integration with the public puppet forge api
to:

- Search for packages
- Fetch packages
- Build spec files out of module metadata
- Automatically build RPMs and SRPMS

It's not a terribly long or complicated piece of software, but it does save on
boilerplate

Usage
-----

    ./pf2rpm - APPLICATION APPLICATION_PARAMS [OPTIONS]
    
    Applications
        search TERM   search for a package
    
        create PKG    create rpms for the given package and it's dependencies.
                      This always downloads all necessary tarballs and builds spec
                      files.  By default no rpms or srpms are produced
    
            --repo    the repository to work in
            --srpm    build srpms
            --rpm     build rpms
    
    Options
        --forge       url serving the puppet forge api
        --help        this help notice
    
    Debugging
        --verbose     High level messages
        --debug       Low level messages

Details
-------

Two puppet forge APIs are queried as part of pf2rpm:

- search - modules.json
- dependency info - api/v1/releases.json

In addition, we process the metadata.json file that comes with each puppet
forge module to gather things like description, summary and license for
inclusion into the spec file.

Project
-------

The main hosting for this project exists at: http://github.com/hanumantmk/pf2rpm
