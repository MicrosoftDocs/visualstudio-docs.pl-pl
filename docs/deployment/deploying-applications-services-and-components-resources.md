---
title: Przegląd wdrożenia | Microsoft Docs
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
ms.openlocfilehash: ff5091a7ca7136cd8b62f75ee7f317b1e5b1f3be
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84173733"
---
# <a name="overview-of-deployment-in-visual-studio"></a>Omówienie wdrażania w programie Visual Studio

Wdrażanie aplikacji, usług i składników to rozpowszechnianie ich w celu instalacji na innych komputerach, urządzeniach, serwerach lub w chmurze. W programie Visual Studio możesz wybrać odpowiednią metodę w zależności od typu wdrożenia, jakiego potrzebujesz.

W przypadku wielu typowych typów aplikacji można wdrożyć aplikację bezpośrednio z poziomu Eksplorator rozwiązań w programie Visual Studio. Aby zapoznać się z szybkim samouczkiem dotyczącym tej funkcji, zobacz [pierwsze spojrzenie na wdrażanie](../deployment/deploying-applications-services-and-components.md).

![Wybierz opcję publikowania](../deployment/media/quickstart-publish-dialog.png)

## <a name="what-publishing-options-are-right-for-me"></a>Jakie opcje publikowania są odpowiednie dla mnie?

W programie Visual Studio aplikacje można publikować bezpośrednio w następujących celach:

- [Azure](#azure)
- [Container Registry platformy Docker](#docker-container-registry)
- [Folder](#folder)
- [Niestandardowe elementy docelowe (IIS, FTP)](#Custom targets (IIS, FTP))

Na karcie **Publikowanie** można wybrać istniejący profil publikowania, zaimportować istniejący lub utworzyć nowy, korzystając z opcji opisanych tutaj. Aby zapoznać się z opcjami publikowania w środowisku IDE dla różnych typów aplikacji, zobacz [pierwsze spojrzenie na wdrożenie](../deployment/deploying-applications-services-and-components.md).

## <a name="azure"></a>Azure 

### <a name="azure-app-service"></a>Azure App Service

[Azure App Service](/azure/app-service/app-service-web-overview) , które ułatwiają deweloperom szybkie tworzenie skalowalnych aplikacji sieci Web i usług bez konieczności utrzymywania infrastruktury. App Service działa na maszynach wirtualnych hostowanych w chmurze na platformie Azure, ale te maszyny wirtualne są zarządzane przez Ciebie. Dla każdej aplikacji w App Service zostanie przypisany unikatowy \* adres URL. azurewebsites.NET; wszystkie warstwy cenowe inne niż bezpłatna umożliwiają przypisanie niestandardowych nazw domen do lokacji.

Należy określić, ile mocy obliczeniowej ma App Service, wybierając [warstwę cenową lub plan](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) dla App Service zawierającej. Można mieć wiele aplikacji sieci Web (i innych typów aplikacji), które współużytkują tę samą App Service bez zmiany warstwy cenowej. Na przykład możesz hostować aplikacje sieci Web do tworzenia, przemieszczania i produkcji w tym samym App Service.

### <a name="when-to-choose-azure-app-service"></a>Kiedy należy wybrać Azure App Service

- Chcesz wdrożyć aplikację sieci Web, która jest dostępna za pomocą Internetu.
- Chcesz automatycznie skalować aplikację sieci Web zgodnie z zapotrzebowaniem bez konieczności ponownego wdrażania.
- Nie chcesz zachować infrastruktury serwera (w tym aktualizacji oprogramowania).
- Na serwerach, na których jest hostowana aplikacja sieci Web, nie są wymagane żadne dostosowania na poziomie komputera.

> Jeśli chcesz używać Azure App Service we własnym centrum danych lub na innych komputerach lokalnych, możesz to zrobić przy użyciu [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

Aby uzyskać więcej informacji o publikowaniu do App Service, zobacz [Przewodnik Szybki Start — publikowanie w usłudze Azure App Service](quickstart-deploy-to-azure.md) i [szybki start — publikowanie ASP.NET Core w systemie Linux](quickstart-deploy-to-linux.md).

### <a name="azure-virtual-machines"></a>Azure Virtual Machines

[Usługa Azure Virtual Machines (maszyny wirtualne)](https://azure.microsoft.com/documentation/services/virtual-machines/) umożliwia tworzenie dowolnej liczby zasobów obliczeniowych w chmurze i zarządzanie nią. Przy założeniu, że odpowiedzialność za wszystkie oprogramowanie i aktualizacje na maszynach wirtualnych, można dostosować je tak długo, jak jest to wymagane przez aplikację. Dostęp do maszyn wirtualnych można uzyskać bezpośrednio za pomocą Pulpit zdalny, a każda z nich będzie obsługiwać przypisany adres IP, tak długo, jak to konieczne.

Skalowanie aplikacji hostowanej na maszynach wirtualnych obejmuje rozmieszczenie dodatkowych maszyn wirtualnych zgodnie z zapotrzebowaniem, a następnie wdrożenie niezbędnego oprogramowania. Ten dodatkowy poziom kontroli umożliwia skalowanie w różny sposób w różnych regionach globalnych. Na przykład jeśli aplikacja obsługuje pracowników w różnych biurach regionalnych, można skalować maszyny wirtualne zgodnie z liczbą pracowników w tych regionach, co może powodować obniżenie kosztów.

Dodatkowe informacje znajdują się w [szczegółowym porównaniu](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/) między Azure App Service, Azure Virtual Machines i innymi usługami platformy Azure, których można użyć jako celu wdrożenia przy użyciu opcji niestandardowej w programie Visual Studio.

### <a name="when-to-choose-azure-app-virtual-machines"></a>Kiedy należy wybrać usługę Azure App Virtual Machines

- Chcesz wdrożyć aplikację sieci Web, która jest dostępna za pośrednictwem Internetu, z pełną kontrolą nad okresem istnienia przypisanych adresów IP.
- Na serwerach programu wymagane są dostosowania na poziomie komputera, w tym dodatkowe oprogramowanie, takie jak wyspecjalizowany system bazy danych, konkretne konfiguracje sieci, partycje dysku i tak dalej.
- Chcesz mieć precyzyjną kontrolę nad skalowaniem aplikacji sieci Web.
- Potrzebujesz bezpośredniego dostępu do serwerów obsługujących aplikację z dowolnego innego powodu.

> Jeśli chcesz korzystać z usługi Azure Virtual Machines we własnym centrum danych lub na innych komputerach lokalnych, możesz to zrobić przy użyciu [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

## <a name="docker-container-registry"></a>Container Registry platformy Docker

Jeśli aplikacja korzysta z platformy Docker, można opublikować aplikację z kontenerem w Container Registry Docker.

### <a name="when-to-choose-docker-container-registry"></a>Kiedy należy wybrać Container Registry platformy Docker

- Chcesz wdrożyć aplikację mającą kontener

## <a name="folder"></a>Folder

Wdrożenie w systemie plików oznacza, że wystarczy skopiować pliki aplikacji do określonego folderu na swoim komputerze. Jest to najczęściej używane do celów testowych lub do wdrożenia aplikacji do użytku przez ograniczoną liczbę osób, jeśli na komputerze jest również uruchomiony serwer. Jeśli folder docelowy jest udostępniony w sieci, wdrożenie w systemie plików może udostępnić pliki aplikacji sieci Web innym użytkownikom, którzy mogą następnie wdrożyć ją na określonych serwerach.

Wszystkie maszyny lokalne, na których działa serwer, mogą udostępnić aplikację za pośrednictwem Internetu lub intranetu w zależności od konfiguracji i sieci, z którymi są połączone. (Jeśli komputer zostanie połączony bezpośrednio z Internetem, należy szczególnie uważnie chronić go przed zagrożeniami bezpieczeństwa zewnętrznego). Ponieważ zarządzasz tymi maszynami, masz pełną kontrolę nad konfiguracjami oprogramowania i sprzętu.

Należy pamiętać, że jeśli z jakiegokolwiek powodu (na przykład dostęp do komputera) nie można korzystać z usług w chmurze, takich jak Azure App Service lub Azure Virtual Machines, można użyć [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) we własnym centrum danych. Azure Stack pozwala zarządzać zasobami obliczeniowymi i korzystać z nich za pomocą Azure App Service i Virtual Machines platformy Azure, jednocześnie zachowując wszystkie dane lokalne.

### <a name="when-to-choose-file-system-deployment"></a>Kiedy należy wybrać wdrożenie systemu plików

- Aplikację należy wdrożyć tylko w udziale plików, z którego inne będą wdrażać je na różnych serwerach.
- Wymagane jest tylko lokalne wdrożenie testowe.
- Chcesz przeanalizować i potencjalnie zmodyfikować pliki aplikacji niezależnie przed ich wysłaniem do innego celu wdrożenia.

Aby uzyskać więcej informacji, zobacz [Przewodnik Szybki Start — wdrażanie do folderu lokalnego](quickstart-deploy-to-local-folder.md) .

## <a name="custom-targets-iis-ftp"></a>Niestandardowe elementy docelowe (IIS, FTP)

Niestandardowy obiekt docelowy pozwala wdrożyć aplikację w miejscu docelowym innym niż Azure App Service, Virtual Machines platformy Azure lub lokalnym systemie plików. Można ją wdrożyć w systemie plików lub na dowolnym innym serwerze (Internet lub intranecie), do którego masz dostęp, w tym także w innych usługach w chmurze. Może współpracować z programem Web Deploy (pliki lub. ZIP) i FTP.

W przypadku wybrania niestandardowego celu program Visual Studio poprosi o podanie nazwy profilu, a następnie zbiera dodatkowe informacje o **połączeniu** , w tym serwer docelowy lub lokalizację, nazwę lokacji i poświadczenia. Na karcie **Ustawienia** można kontrolować następujące zachowania:

- Konfiguracja, którą chcesz wdrożyć.
- Czy usunąć istniejące pliki z lokalizacji docelowej.
- Czy należy prekompilować podczas publikowania.
- Określa, czy pliki w folderze App_Data mają być wykluczone z wdrożenia.

W programie Visual Studio można utworzyć dowolną liczbę niestandardowych profilów wdrożenia, co umożliwia zarządzanie profilami przy użyciu różnych ustawień.

### <a name="when-to-choose-custom-deployment"></a>Kiedy należy wybrać wdrożenie niestandardowe

- Używasz usług w chmurze na dostawcy innym niż Azure, do którego można uzyskać dostęp za pośrednictwem adresów URL.
- Chcesz wdrożyć przy użyciu poświadczeń innych niż te, które są używane w programie Visual Studio, lub powiązane bezpośrednio z kontami platformy Azure.
- Chcesz usunąć pliki z obiektu docelowego przy każdym wdrożeniu.

Aby uzyskać więcej informacji, zobacz [Przewodnik Szybki Start — wdrażanie w witrynie sieci Web](quickstart-deploy-to-a-web-site.md) .

## <a name="next-steps"></a>Następne kroki

Samouczki:

- [Wdrażanie aplikacji .NET Core za pomocą narzędzia do publikowania](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikowanie aplikacji ASP.NET Core na platformie Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Wdrożenie w Visual C++](/cpp/windows/deployment-in-visual-cpp)
- [Wdrażanie aplikacji platformy UWP](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikowanie aplikacji node. js na platformie Azure przy użyciu Web Deploy](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikowanie aplikacji w języku Python w celu Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
