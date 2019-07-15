# Test2::Tools::URL [![Build Status](https://secure.travis-ci.org/plicease/Test2-Tools-URL.png)](http://travis-ci.org/plicease/Test2-Tools-URL)

Compare a URL in your Test2 test

# SYNOPSIS

    use Test2::V0;
    use Test2::Tools::URL;
    
    is(
      "http://example.com/path1/path2?query=1#fragment",
      url {
        url_component scheme   => 'http';
        url_component host     => 'example.com';
        url_component path     => '/path1/path2';
        url_component query    => { query => 1 };
        url_component fragment => 'fragment';
      },
      'url is as expected',
    );

# DESCRIPTION

This set of [Test2](https://metacpan.org/pod/Test2) tools helps writing tests against
URLs, represented as either strings, or as objects that
stringify to URLs (such as [URI](https://metacpan.org/pod/URI) or [Mojo::URL](https://metacpan.org/pod/Mojo::URL)).

The idea is that you may be writing tests against URLs,
but you may only care about one or two components, and
you may not want to worry about decoding the URL or breaking
the components up.  The URL may be nested deeply.  This
tool is intended to help!

# FUNCTIONS

## url

    my $check = url {}

Checks that the given string or object is a valid URL.

## url\_base

    url {
      url_base $url;
    };

Use the given base URL for relative paths.  If specified outside of a URL,
then it will apply to all url checks.

## url\_component

    url {
      url_component $component, $check;
    }

Check that the given URL component matches.

- scheme
- authority
- userinfo
- hostport
- host
- port
- path
- query

    May be either a string, list or array!

- fragment

# SEE ALSO

[Test2::Suite](https://metacpan.org/pod/Test2::Suite)

# AUTHOR

Author: Graham Ollis <plicease@cpan.org>

Contributors:

Paul Durden (alabamapaul, PDURDEN)

# COPYRIGHT AND LICENSE

This software is copyright (c) 2017 by Graham Ollis.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
