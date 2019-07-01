FROM mcr.microsoft.com/dotnet/core/aspnet:2.2 

MAINTAINER "Kräml, Marcel / Vleugels, Rene"

RUN apt-get update \
&& mkdir software \
&& cd software \
&& apt-get install --no-install-recommends --no-install-suggests -y unzip wget ca-certificates \
&& wget https://github.com/hemane/Backend/releases/download/b2/linuxarm.zip \
&& unzip linuxarm.zip \
&& rm linuxarm.zip

EXPOSE 80

STOPSIGNAL SIGTERM

WORKDIR /software

CMD ["dotnet", "/software/HeMaNe.Web.dll"]
