---
title: Omówienie wdrażania | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 06/22/2018
ms.topic: overview
dev_langs:
- FSharp
- VB
- CSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b7c322b960360231c2e8a1d2aa1a9920bbcf5521
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409367"
---
# <a name="overview-of-deployment-in-visual-studio"></a>Omówienie wdrażania w programie Visual Studio

Wdrażanie aplikacji, usług i składników to rozpowszechnianie ich w celu instalacji na innych komputerach, urządzeniach, serwerach lub w chmurze. W programie Visual Studio możesz wybrać odpowiednią metodę w zależności od typu wdrożenia, jakiego potrzebujesz.

Dla wielu popularnych typów aplikacji można wdrożyć swojej aplikacji bezpośrednio z Eksploratora rozwiązań w programie Visual Studio. Aby zapoznać się z szybkim samouczkiem dotyczącym tej funkcji, zobacz [pierwsze spojrzenie na wdrażanie](../deployment/deploying-applications-services-and-components.md).

![Wybierz jedną z opcji publikowania](../deployment/media/quickstart-publish-azure.png)

## <a name="what-publishing-options-are-right-for-me"></a>Jakie opcje publikowania są dla mnie odpowiednia?

Z poziomu programu Visual Studio, aplikacje mogą być publikowane bezpośrednio do następujących celów:

- [Azure App Service](#azure-app-service)
- [Azure Virtual Machines](#azure-virtual-machines)
- [System plików](#file-system)
- [Niestandardowe elementy docelowe (IIS, FTP itp.)](#custom-targets-iis-ftp), które obejmują wszystkie dowolne serwery sieci Web.

Na karcie **Publikowanie** można wybrać istniejący profil publikowania, zaimportować istniejący lub utworzyć nowy, korzystając z opcji opisanych tutaj. Aby zapoznać się z opcjami publikowania w środowisku IDE dla różnych typów aplikacji, zobacz [pierwsze spojrzenie na wdrożenie](../deployment/deploying-applications-services-and-components.md).

## <a name="azure-app-service"></a>Azure App Service

[Azure App Service](/azure/app-service/app-service-web-overview) i [App Service w systemie Linux](/azure/app-service/containers/app-service-linux-intro) pomagają deweloperom szybko tworzyć różne skalowalne aplikacje i usługi sieci Web bez konieczności utrzymywania infrastruktury.

Należy określić, ile mocy obliczeniowej ma App Service, wybierając [warstwę cenową lub plan](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) dla App Service zawierającej. Może mieć wiele sieci Web apps (i innych typów aplikacji) udostępnianie tej samej usługi App Service bez konieczności zmieniania warstwy cenowej. Na przykład umożliwia hostowanie aplikacji sieci Web w rozwoju, przejściowe i produkcyjne razem na tej samej usługi App Service.

Usługi App Service działa w przypadku hostowanych w chmurze maszyn wirtualnych na platformie Azure, ale te maszyny wirtualne są zarządzane dla Ciebie. Dla każdej aplikacji w App Service zostanie przypisany unikatowy adres URL \*. azurewebsites.net; wszystkie warstwy cenowe inne niż bezpłatna umożliwiają przypisanie niestandardowych nazw domen do lokacji.

### <a name="when-to-choose-azure-app-service"></a>Kiedy należy wybrać w usłudze Azure App Service

- Chcesz wdrożyć aplikację internetową, która jest dostępna za pośrednictwem Internetu.
- Chcesz automatycznie skalować swoją aplikację sieci web, odpowiednio do zapotrzebowania bez konieczności ponownego wdrażania.
- Nie chcesz do obsługi infrastruktury serwera (w tym aktualizacji oprogramowania).
- Wszelkie dostosowania na poziomie maszyny, na serwerach, które hostują aplikację sieci web nie jest konieczne.

> Jeśli chcesz używać Azure App Service we własnym centrum danych lub na innych komputerach lokalnych, możesz to zrobić przy użyciu [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

Aby uzyskać więcej informacji o publikowaniu do App Service, zobacz [Przewodnik Szybki Start — publikowanie w usłudze Azure App Service](quickstart-deploy-to-azure.md) i [szybki start — publikowanie ASP.NET Core w systemie Linux](quickstart-deploy-to-linux.md).

## <a name="azure-virtual-machines"></a>Azure Virtual Machines

[Usługa Azure Virtual Machines (maszyny wirtualne)](https://azure.microsoft.com/documentation/services/virtual-machines/) umożliwia tworzenie dowolnej liczby zasobów obliczeniowych w chmurze i zarządzanie nią. Przy założeniu, odpowiedzialność za wszystkie aktualizacji oprogramowania i na maszynach wirtualnych, można dostosować je wedle potrzeby zgodnie z wymaganiami aplikacji. Dostęp do maszyn wirtualnych bezpośrednio za pośrednictwem pulpitu zdalnego, a każdy z nich będzie stosować jej przypisany adres IP, tak długo, jak żądany.

Skalowanie aplikacji, która jest obsługiwana na maszynach wirtualnych obejmuje wdrażanie dodatkowych maszyn wirtualnych, odpowiednio do zapotrzebowania, a następnie wdrożenie niezbędne oprogramowanie. Ten dodatkowy poziom kontroli umożliwia skalowanie inaczej w różnych regionach na świecie. Na przykład aplikacji obsługujących pracowników w różnych biur regionalnych można skalować zgodnie z liczbą pracowników w tych regionach potencjalnie obniżając koszty maszyn wirtualnych.

Dodatkowe informacje znajdują się w [szczegółowym porównaniu](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/) między Azure App Service, Azure Virtual Machines i innymi usługami platformy Azure, których można użyć jako celu wdrożenia przy użyciu opcji niestandardowej w programie Visual Studio.

### <a name="when-to-choose-azure-app-virtual-machines"></a>Kiedy należy wybrać maszyny wirtualne aplikacji platformy Azure

- Chcesz wdrożyć aplikację internetową, która jest dostępna za pośrednictwem Internetu z pełną kontrolę nad okresem istnienia przydzielonych adresów IP.
- Należy dostosowań na poziomie komputera na serwerach, który zawiera dodatkowe oprogramowanie, takie jak system wyspecjalizowane bazie danych, określonej sieci, konfiguracji, partycji dysku i tak dalej.
- Chcesz, aby poprawnie poziom kontroli nad skalowanie aplikacji sieci web.
- Należy bezpośredni dostęp do serwerów obsługujących aplikację z innych przyczyn.

> Jeśli chcesz korzystać z usługi Azure Virtual Machines we własnym centrum danych lub na innych komputerach lokalnych, możesz to zrobić przy użyciu [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

## <a name="file-system"></a>System plików

Wdrażanie w systemie plików oznacza, że można po prostu skopiować plików aplikacji do określonego folderu na swoim komputerze. W większości przypadków służy do celów testowych lub aby wdrożyć aplikację do użytku przez ograniczoną liczbę osób, jeśli komputer jest również korzysta z serwera. Jeśli folder docelowy jest udostępniony w sieci, potem wdrożyć w systemie plików można udostępnić sieci web plików aplikacji do innych użytkowników, którzy mogą następnie wdrożyć ją do określonych serwerów.

Komputerach lokalnych, które działają na serwerze można udostępnić swojej aplikacji za pośrednictwem Internetu lub sieci wewnętrznej, w zależności od sposobu skonfigurowania i sieci, z którymi jest połączony. (Jeśli komputer zostanie połączony bezpośrednio z Internetem, należy szczególnie uważnie chronić go przed zagrożeniami bezpieczeństwa zewnętrznego). Ponieważ zarządzasz tymi maszynami, masz pełną kontrolę nad konfiguracjami oprogramowania i sprzętu.

Należy pamiętać, że jeśli z jakiegokolwiek powodu (na przykład dostęp do komputera) nie można korzystać z usług w chmurze, takich jak Azure App Service lub Azure Virtual Machines, można użyć [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) we własnym centrum danych. Usługi Azure Stack umożliwia zarządzanie zasobami oraz używanie zasobów komputerowych za pośrednictwem usługi Azure App Service i Azure Virtual Machines, zachowując jeszcze wszystkiego w środowisku lokalnym.

### <a name="when-to-choose-file-system-deployment"></a>Kiedy należy wybrać wdrożenie systemu plików

- Należy wdrażać tylko aplikacji w udziale plików, w którym inne osoby wdroży go na innych serwerach.
- Należy tylko wdrożenia lokalnego testu.
- Chcesz zbadać i potencjalnie modyfikować pliki aplikacji niezależnie przed wysłaniem ich na inny cel wdrożenia.

Aby uzyskać więcej informacji, zobacz [Przewodnik Szybki Start — wdrażanie do folderu lokalnego](quickstart-deploy-to-local-folder.md) .

## <a name="custom-targets-iis-ftp"></a>Niestandardowe obiekty docelowe (usługi IIS, FTP)

Niestandardowe obiekty docelowe pozwala wdrożyć aplikację na docelowym niż w usłudze Azure App Service, Azure Virtual Machines lub lokalnego systemu plików. System plików lub dowolnego innego serwera (Internet lub Intranet) do którego masz dostęp, włączając te na innych usługach w chmurze można wdrożyć. Można pracować w sieci web wdrażanie (plików lub. ZIP) i FTP.

W przypadku wybrania niestandardowego celu program Visual Studio poprosi o podanie nazwy profilu, a następnie zbiera dodatkowe informacje o **połączeniu** , w tym serwer docelowy lub lokalizację, nazwę lokacji i poświadczenia. Na karcie **Ustawienia** można kontrolować następujące zachowania:

- Konfiguracja, który chcesz wdrożyć.
- Czy chcesz usunąć istniejące pliki z miejsca docelowego.
- Określa, czy wstępna kompilacja podczas publikowania.
- Określa, czy wykluczyć pliki w folderze App_Data z wdrożenia.

Można utworzyć dowolną liczbę profilów wdrażania niestandardowego w programie Visual Studio, co umożliwia zarządzanie profilami z różnymi ustawieniami.

### <a name="when-to-choose-custom-deployment"></a>Kiedy należy wybrać wdrożenia niestandardowego

- Używasz usług w chmurze dla dostawcy innego niż Azure, który jest możliwy za pośrednictwem adresów URL.
- Chcesz wdrożyć, korzystając z poświadczeń innych niż te, które można używać w programie Visual Studio lub te bezpośrednio związane z Twojego konta platformy Azure.
- Chcesz usunąć pliki z docelowym każdorazowo, gdy wdrożysz.

Aby uzyskać więcej informacji, zobacz [Przewodnik Szybki Start — wdrażanie w witrynie sieci Web](quickstart-deploy-to-a-web-site.md) .

## <a name="next-steps"></a>Następne kroki

Samouczki:

- [Wdrażanie aplikacji .NET Core za pomocą narzędzia do publikowania](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikowanie aplikacji ASP.NET Core na platformie Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Wdrażanie w Visual C++](/cpp/windows/deployment-in-visual-cpp)
- [Wdrażanie aplikacji platformy UWP](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikowanie aplikacji node. js na platformie Azure przy użyciu Web Deploy](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikowanie aplikacji w języku Python w celu Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
