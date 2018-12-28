---
title: Omówienie wdrażania | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 06/22/2018
ms.technology: vs-ide-deployment
ms.topic: overview
dev_langs:
- FSharp
- VB
- CSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d578dcf3702b340adcbef36002b64b20f65a5c73
ms.sourcegitcommit: 935e341a02dba1c2aa3b6e89469388aa6e626f7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53684239"
---
# <a name="overview-of-deployment-in-visual-studio"></a>Omówienie wdrażania w programie Visual Studio

Wdrażanie aplikacji, usług i składników to rozpowszechnianie ich w celu instalacji na innych komputerach, urządzeniach, serwerach lub w chmurze. W programie Visual Studio możesz wybrać odpowiednią metodę w zależności od typu wdrożenia, jakiego potrzebujesz.

Dla wielu popularnych typów aplikacji można wdrożyć swojej aplikacji bezpośrednio z Eksploratora rozwiązań w programie Visual Studio. Aby szybko zapoznać się z tej możliwości, zobacz [Pierwsze spojrzenie na wdrażanie](../deployment/deploying-applications-services-and-components.md).

![Wybierz jedną z opcji publikowania](../deployment/media/quickstart-publish-azure.png)

## <a name="what-publishing-options-are-right-for-me"></a>Jakie opcje publikowania są dla mnie odpowiednia?

Z poziomu programu Visual Studio, aplikacje mogą być publikowane bezpośrednio do następujących celów:

- [Usługa Azure App Service](#azure-app-service)
- [Usługa Azure Virtual Machines](#azure-virtual-machines)
- [System plików](#file-system)
- [Niestandardowe obiekty docelowe (usługi IIS, FTP itp.) ](#custom-targets), która obejmuje wszystkie serwery sieci web dowolnego.

Na **Publikuj** karty, wybierz istniejący profil publikowania, zaimportuj istniejącą lub Utwórz nową za pomocą opcji opisanych w tym miejscu. Aby zapoznać się z opcji publikowania w środowisku IDE dla różnych typów aplikacji, zobacz [Pierwsze spojrzenie na wdrażanie](../deployment/deploying-applications-services-and-components.md).

## <a name="azure-app-service"></a>Usługa Azure App Service

[Usługa Azure App Service](/azure/app-service/app-service-web-overview) i [usługi App Service w systemie Linux](/azure/app-service/containers/app-service-linux-intro) ułatwiają deweloperom szybkie tworzenie różnych skalowalnych aplikacji i usług bez konserwacja infrastruktury.

Możesz określić, ile obliczeń power usługi App Service ma, wybierając [ceny warstwy lub planu](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) dla zawierającego usługi App Service. Może mieć wiele sieci Web apps (i innych typów aplikacji) udostępnianie tej samej usługi App Service bez konieczności zmieniania warstwy cenowej. Na przykład umożliwia hostowanie aplikacji sieci Web w rozwoju, przejściowe i produkcyjne razem na tej samej usługi App Service.

Usługi App Service działa w przypadku hostowanych w chmurze maszyn wirtualnych na platformie Azure, ale te maszyny wirtualne są zarządzane dla Ciebie. Każda aplikacja w usłudze App Service zostanie przypisany unikatowy \*. adresu URL azurewebsites.net; wszystkie warstwy cenowe innych niż bezpłatna umożliwia przypisywanie nazw domen niestandardowych do lokacji.

### <a name="when-to-choose-azure-app-service"></a>Kiedy należy wybrać w usłudze Azure App Service

- Chcesz wdrożyć aplikację internetową, która jest dostępna za pośrednictwem Internetu.
- Chcesz automatycznie skalować swoją aplikację sieci web, odpowiednio do zapotrzebowania bez konieczności ponownego wdrażania.
- Nie chcesz do obsługi infrastruktury serwera (w tym aktualizacji oprogramowania).
- Wszelkie dostosowania na poziomie maszyny, na serwerach, które hostują aplikację sieci web nie jest konieczne.

> Jeśli chcesz używać usługi Azure App Service w Twoim centrum danych lub innymi komputerami w środowisku lokalnym, możesz to zrobić za pomocą [usługi Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

Aby uzyskać więcej informacji dotyczących publikowania w usłudze App Service, zobacz [Szybki Start — publikowanie w usłudze Azure App Service](quickstart-deploy-to-azure.md) i [Szybki Start — publikowanie platformy ASP.NET Core z systemem Linux](quickstart-deploy-to-linux.md).

## <a name="azure-virtual-machines"></a>Usługa Azure Virtual Machines

[Azure Virtual Machines (VMs)](https://azure.microsoft.com/documentation/services/virtual-machines/) pozwalają na tworzenie i zarządzanie nimi dowolną liczbę zasobów obliczeniowych w chmurze. Przy założeniu, odpowiedzialność za wszystkie aktualizacji oprogramowania i na maszynach wirtualnych, można dostosować je wedle potrzeby zgodnie z wymaganiami aplikacji. Dostęp do maszyn wirtualnych bezpośrednio za pośrednictwem pulpitu zdalnego, a każdy z nich będzie stosować jej przypisany adres IP, tak długo, jak żądany.

Skalowanie aplikacji, która jest obsługiwana na maszynach wirtualnych obejmuje wdrażanie dodatkowych maszyn wirtualnych, odpowiednio do zapotrzebowania, a następnie wdrożenie niezbędne oprogramowanie. Ten dodatkowy poziom kontroli umożliwia skalowanie inaczej w różnych regionach na świecie. Na przykład aplikacji obsługujących pracowników w różnych biur regionalnych można skalować zgodnie z liczbą pracowników w tych regionach potencjalnie obniżając koszty maszyn wirtualnych.

Aby uzyskać dodatkowe informacje, zapoznaj się [szczegółowe porównanie](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/) między usługi Azure App Service, Azure Virtual Machines i innych usług platformy Azure, które służą jako cel wdrożenia przy użyciu opcji niestandardowych w programie Visual Studio.

### <a name="when-to-choose-azure-app-virtual-machines"></a>Kiedy należy wybrać maszyny wirtualne aplikacji platformy Azure

- Chcesz wdrożyć aplikację internetową, która jest dostępna za pośrednictwem Internetu z pełną kontrolę nad okresem istnienia przydzielonych adresów IP.
- Należy dostosowań na poziomie komputera na serwerach, który zawiera dodatkowe oprogramowanie, takie jak system wyspecjalizowane bazie danych, określonej sieci, konfiguracji, partycji dysku i tak dalej.
- Chcesz, aby poprawnie poziom kontroli nad skalowanie aplikacji sieci web.
- Należy bezpośredni dostęp do serwerów obsługujących aplikację z innych przyczyn.

> Jeśli chcesz użyć usługi Azure Virtual Machines w Twoim centrum danych lub innymi komputerami w środowisku lokalnym, możesz to zrobić za pomocą [usługi Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

## <a name="file-system"></a>System plików

Wdrażanie w systemie plików oznacza, że można po prostu skopiować plików aplikacji do określonego folderu na swoim komputerze. W większości przypadków służy do celów testowych lub aby wdrożyć aplikację do użytku przez ograniczoną liczbę osób, jeśli komputer jest również korzysta z serwera. Jeśli folder docelowy jest udostępniony w sieci, potem wdrożyć w systemie plików można udostępnić sieci web plików aplikacji do innych użytkowników, którzy mogą następnie wdrożyć ją do określonych serwerów.

Komputerach lokalnych, które działają na serwerze można udostępnić swojej aplikacji za pośrednictwem Internetu lub sieci wewnętrznej, w zależności od sposobu skonfigurowania i sieci, z którymi jest połączony. (W przypadku podłączenia komputera bezpośrednio do Internetu, być szczególnie uważać, aby chronić je przed zagrożeniami bezpieczeństwa zewnętrznych). Ponieważ można zarządzać tymi komputerami, masz pełną kontrolę nad konfiguracjach sprzętu i oprogramowania.

Należy pamiętać, że jeśli jakiegokolwiek powodu (na przykład dostęp do komputera) nie jest możliwe do użycia usług cloud services, takich jak usługa Azure App Service lub Azure Virtual Machines, możesz użyć [usługi Azure Stack](https://azure.microsoft.com/overview/azure-stack/) we własnym centrum danych. Usługi Azure Stack umożliwia zarządzanie zasobami oraz używanie zasobów komputerowych za pośrednictwem usługi Azure App Service i Azure Virtual Machines, zachowując jeszcze wszystkiego w środowisku lokalnym.

### <a name="when-to-choose-file-system-deployment"></a>Kiedy należy wybrać wdrożenie systemu plików

- Należy wdrażać tylko aplikacji w udziale plików, w którym inne osoby wdroży go na innych serwerach.
- Należy tylko wdrożenia lokalnego testu.
- Chcesz zbadać i potencjalnie modyfikować pliki aplikacji niezależnie przed wysłaniem ich na inny cel wdrożenia.

Aby uzyskać więcej informacji, zobacz [Szybki Start — wdrażanie w folderze lokalnym](quickstart-deploy-to-local-folder.md)

## <a name="custom-targets-iis-ftp"></a>Niestandardowe obiekty docelowe (usługi IIS, FTP)

Niestandardowe obiekty docelowe pozwala wdrożyć aplikację na docelowym niż w usłudze Azure App Service, Azure Virtual Machines lub lokalnego systemu plików. System plików lub dowolnego innego serwera (Internet lub Intranet) do którego masz dostęp, włączając te na innych usługach w chmurze można wdrożyć. Można pracować w sieci web wdrażanie (plików lub. ZIP) i FTP.

Podczas wybierania niestandardowe obiekty docelowe, Visual Studio wyświetli monit o podanie nazwa profilu, a następnie zbieranie dodatkowych **połączenia** informacje w tym serwera docelowego lub lokalizacji, nazwa witryny i poświadczenia. Możesz kontrolować następujące zachowania na **ustawienia** karty:

- Konfiguracja, który chcesz wdrożyć.
- Czy chcesz usunąć istniejące pliki z miejsca docelowego.
- Określa, czy wstępna kompilacja podczas publikowania.
- Określa, czy wykluczyć pliki w folderze App_Data z wdrożenia.

Można utworzyć dowolną liczbę profilów wdrażania niestandardowego w programie Visual Studio, co umożliwia zarządzanie profilami z różnymi ustawieniami.

### <a name="when-to-choose-custom-deployment"></a>Kiedy należy wybrać wdrożenia niestandardowego

- Używasz usług w chmurze dla dostawcy innego niż Azure, który jest możliwy za pośrednictwem adresów URL.
- Chcesz wdrożyć, korzystając z poświadczeń innych niż te, które można używać w programie Visual Studio lub te bezpośrednio związane z Twojego konta platformy Azure.
- Chcesz usunąć pliki z docelowym każdorazowo, gdy wdrożysz.

Aby uzyskać więcej informacji, zobacz [Szybki Start — wdrażanie w witrynie sieci web](quickstart-deploy-to-a-web-site.md)

## <a name="next-steps"></a>Następne kroki

Samouczki:

- [Wdrażanie aplikacji .NET Core za pomocą narzędzia publikowania](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikowanie aplikacji platformy ASP.NET core na platformie Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Wdrażanie w Visual C++](/cpp/ide/deployment-in-visual-cpp)
- [Wdrażanie aplikacji platformy uniwersalnej systemu Windows](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikowanie aplikacji w języku Node.js na platformie Azure, za pomocą narzędzia Web Deploy](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikowanie aplikacji w języku Python w usłudze Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
