# nginx-hda-bundle
#### Modules included 
  1. Dynamic modules
- [headers-more-nginx](https://github.com/openresty/headers-more-nginx-module)
- [lua-nginx](https://github.com/openresty/lua-nginx-module)
- [naxsi](https://github.com/nbs-system/naxsi) with pull 258 patch
- [nginx-length-hiding-filter](https://github.com/nulab/nginx-length-hiding-filter-module)
- [nginx_session_binding_proxy](https://github.com/wburgers/Session-Binding-Proxy)
- [ngx_devel_kit](https://github.com/simpl/ngx_devel_kit)
- [ngx_pagespeed](https://github.com/pagespeed/ngx_pagespeed)
- [rds-json-nginx](https://github.com/openresty/rds-json-nginx-module) with pull 4 patch
- [testcookie-nginx](https://github.com/kyprizel/testcookie-nginx-module)
- [nginx-upstream-order](https://github.com/flygoast/ngx_http_upstream_order)
  2. Static modules  
- [ngx_postgres module](https://github.com/FRiCKLE/ngx_postgres) with pull 24 patch

  > Note: I hope it will be dynamic soon too.

  3. Base dynamic modules
- http_xslt module
- http_image_filter module
- http_geoip module
- http_perl module
- ngx_http_js module

  4. Static modules
- http_ssl module
- http_realip module
- http_addition module
- http_sub module
- http_gunzip module
- http_gzip_static module
- http_random_index module
- http_secure_link module
- http_stub_status module
- http_auth_request module
- stream_ssl module
- http_slice module

Modules removed: http_dav, http_flv, http_mp4

####Optimizations made
* Server version changed to cloudflare-nginx
* [TLS TTFB optimization](https://www.igvita.com/2013/12/16/optimizing-nginx-tls-time-to-first-byte/)
  > Note:1360 buffer size used instead 1400.

- How-to load dynamic modules?
Add the following to to the top of /etc/nginx/nginx.conf (for example after pid) and reload nginx:
load_module modules/ndk_http_module.so;
load_module modules/ngx_http_geoip_module.so;
load_module modules/ngx_http_headers_more_filter_module.so;
load_module modules/ngx_http_image_filter_module.so;
load_module modules/ngx_http_length_hiding_filter_module.so;
load_module modules/ngx_http_lua_module.so;
load_module modules/ngx_http_naxsi_module.so;
load_module modules/ngx_http_njs_filter_module.so;
load_module modules/ngx_pagespeed.so;
load_module modules/ngx_http_perl_module.so;
load_module modules/ngx_http_rds_json_filter_module.so;
load_module modules/ngx_http_session_binding_proxy_module.so;
load_module modules/ngx_http_testcookie_access_module.so;
load_module modules/ngx_http_upstream_order_module.so;
load_module modules/ngx_http_xslt_filter_module.so;
Note: Use only modules you need to use. With dynamic modules this is pretty easy.
