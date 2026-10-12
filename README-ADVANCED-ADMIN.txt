This edition uses a travel-CMS style workflow: Dashboard -> Vehicles -> Tours -> Media Library -> Homepage -> Content -> SEO -> GitHub Connection.

The design is informed by common travel CMS patterns such as centralized media management, tour/package management and vehicle/fleet profiles. Examples researched for this rebuild include Jaabo's travel CMS modules, a Sri Lankan travel booking dashboard case study, and fleet media-library patterns.

The site remains a static GitHub Pages website. A browser-only admin cannot safely write to a GitHub repository without authenticated GitHub API access, so the Connection page uses a user-supplied fine-grained token stored only in sessionStorage.
