FROM texlive/texlive:TL2018-historic
LABEL org.opencontainers.image.source https://github.com/michals/neo-tex-env

# Install fonts from AdobeReader
RUN curl http://ardownload.adobe.com/pub/adobe/reader/unix/9.x/9.5.5/enu/AdbeRdr9.5.5-1_i386linux_enu.deb > ar9.deb \
    && dpkg -x ar9.deb / \
    && mkdir -p /usr/local/share/fonts/ \
    && cp /opt/Adobe/Reader9/Resource/Font/*.otf /usr/local/share/fonts/ \
    && rm -rf /opt/Adobe ar9.deb

# Update font cache and install gawk
RUN apt-get update \
    && apt-get install -y fontconfig gawk \
    && rm -rf /var/lib/apt/lists/* \
    && fc-cache -fv


