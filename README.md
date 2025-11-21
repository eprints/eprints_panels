EPrints Panels
==============

The 'eprints_panels' ingredient is designed to extend EPrints 3.5 by adding a generic rendering library.
This allows sections of content which typically appear on summary pages for records or users to be rendered in logical groups.
Each panel represents a section.  Panels can be rendered as a set of tiles, or as a set of tabs.

Authors:
- Justin Bradley, EPrints Services

EPrints Panels (`eprints_panels`) is supplied by EPrints Services as an standard ingredient for EPrints 3.5.
EPrints 3.5 is also supplied by EPrints Services.
The files contained within this directory are all Copyright 2025 University of Southampton.

Notes
-----

A simple panel rendering code.

Try calling it from `eprint_render`:

```
$c->{eprint_render} = sub
{
...
  my $panelfn = $c->{eprint_render_panels};
  $page->appendChild( &{$panelfn}( $eprint, $repository ) );
...
};
```


And some test code for hooking in a user profile set of panela into a MePrints homepage

In `lib/plugins/EPrints/Plugin/Screen/User/Homepage.pm` `render()` add

```
my $panelfn = $self->{session}->config("user_render_panels");
$page->appendChild( &{$panelfn}( $user, $self->{session} ) ) if defined($panelfn) && ref($panelfn) eq "CODE";
```
