---
title: Wdrażanie aplikacji Visual Studio w folderze, usługach IIS, na platformie Azure lub w innym miejscu docelowym
titleSuffix: ''
description: Dowiedz się więcej o opcjach publikowania aplikacji przy użyciu narzędzia do publikowania.
ms.custom:
- SEO-VS-2020
- contperf-fy21q1
ms.date: 08/21/2020
ms.topic: troubleshooting
f1_keywords:
- vs.publish
dev_langs:
- FSharp
- VB
- CSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 099bd2c6cc47895c913b3f852835d2fd09d0f9c3
ms.sourcegitcommit: 4e09130bcd55bb9cb8ad157507c23b67aa209fad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2021
ms.locfileid: "113549488"
---
# <a name="deploy-your-app-to-a-folder-iis-azure-or-another-destination"></a>Wdrażanie aplikacji w folderze, usługach IIS, na platformie Azure lub w innym miejscu docelowym

Wdrażanie aplikacji, usług i składników to rozpowszechnianie ich w celu instalacji na innych komputerach, urządzeniach, serwerach lub w chmurze. W programie Visual Studio możesz wybrać odpowiednią metodę w zależności od typu wdrożenia, jakiego potrzebujesz.

Uzyskaj pomoc dla zadania wdrożenia:

- Nie masz pewności, jaką opcję wdrożenia wybrać? Zobacz [Jakie opcje publikowania są dla mnie odpowiednie?](#what-publishing-options-are-right-for-me)
- Aby uzyskać pomoc w zakresie wdrażania usług Azure App Service lub IIS, zobacz Troubleshoot ASP.NET Core on Azure App Service and IIS (Rozwiązywanie problemów z ASP.NET Core [i usługami IIS).](/aspnet/core/test/troubleshoot-azure-iis)
- Aby uzyskać pomoc w konfigurowaniu ustawień wdrażania .NET, zobacz [Konfigurowanie ustawień wdrażania programu .NET.](#configure-net-deployment-settings)
- Aby wdrożyć w nowym celu, jeśli wcześniej utworzono profil publikowania, wybierz pozycję **Nowy** w oknie **Publikowanie** dla skonfigurowanego profilu.

   ![Tworzenie nowego profilu publikowania](../deployment/media/create-a-new-publish-profile.png)

   Następnie wybierz opcję wdrożenia w oknie Publikowanie. Aby uzyskać informacje na temat opcji publikowania, zobacz poniższe sekcje.

## <a name="what-publishing-options-are-right-for-me"></a>Jakie opcje publikowania są dla mnie odpowiednie?

Z poziomu Visual Studio aplikacje można publikować bezpośrednio w następujących celach:

::: moniker range=">=vs-2019"
- [Azure](#azure)
- [Docker Container Registry](#docker-container-registry)
- [Folder](#folder)
- [Serwer FTP/FTPS](#ftpftps-server)
- [Serwer sieci Web (IIS)](#web-server-iis)
- [Importowanie profilu](#import-profile)
::: moniker-end
::: moniker range="vs-2017"
- [App Service](#azure-app-service)
- [App Service dla systemu Linux](#azure-app-service)
- [Usługi IIS (wybierz usługi IIS, FTP itp.)](#web-server-iis)
- [FTP/FTPS (wybierz usługi IIS, FTP itp.)](#ftpftps-server)
- [Folder](#folder)
- [Importowanie profilu](#import-profile)
::: moniker-end

Poprzednie opcje są wyświetlane, jak pokazano na poniższej ilustracji podczas tworzenia nowego profilu publikowania.

::: moniker range=">=vs-2019"
![Wybieranie opcji publikowania](../deployment/media/quickstart-publish-dialog.png)
::: moniker-end
::: moniker range="vs-2017"
![Wybieranie opcji publikowania](../deployment/media/quickstart-publish-dialog-vs-2017.png)
::: moniker-end

Aby uzyskać krótki przewodnik po bardziej ogólnych opcjach wdrażania aplikacji, zobacz [Pierwsze spojrzenie na wdrożenie](../deployment/deploying-applications-services-and-components.md).

## <a name="azure"></a>Azure 

Po wybraniu platformy Azure możesz wybrać między:

- [Azure App Service](#azure-app-service) uruchomione w systemie Windows, Linux lub jako obraz platformy Docker
- Obraz platformy Docker wdrożony w [Azure Container Registry](#azure-container-registry)
- Maszyna [wirtualna platformy Azure](#azure-virtual-machine)

![Wybieranie usługi platformy Azure](../deployment/media/quickstart-choose-azure-service.png)

### <a name="azure-app-service"></a>Azure App Service

[Azure App Service](/azure/app-service/app-service-web-overview) pomaga deweloperom szybko tworzyć skalowalne aplikacje i usługi internetowe bez utrzymywania infrastruktury. Usługa App Service działa na maszynach wirtualnych hostowanych w chmurze na platformie Azure, ale te maszyny wirtualne są zarządzane za Ciebie. Do każdej aplikacji w App Service zostanie przypisany unikatowy adres URL .azurewebsites.net. Wszystkie warstwy cenowe inne niż Bezpłatna umożliwiają przypisywanie niestandardowych nazw domen \* do witryny.

Możesz określić, ile mocy obliczeniowej ma App Service, wybierając warstwę cenową lub [plan](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) dla zasobów App Service. Możesz mieć wiele aplikacji internetowych (i innych typów aplikacji) współużytkuje te same App Service bez zmiany warstwy cenowej. Na przykład możesz hostować aplikacje internetowe w tym samym środowisku dewelopera, przejściowego i produkcyjnego w tym samym App Service.

#### <a name="when-to-choose-azure-app-service"></a>Kiedy należy wybrać Azure App Service

- Chcesz wdrożyć aplikację internetową dostępną przez Internet.
- Chcesz automatycznie skalować aplikację internetową zgodnie z zapotrzebowaniem bez konieczności ponownego jej stosowania.
- Nie chcesz utrzymywać infrastruktury serwera (w tym aktualizacji oprogramowania).
- Na serwerach hostowych aplikację internetową nie są potrzebne żadne dostosowania na poziomie komputera.

> Jeśli chcesz używać Azure App Service we własnym centrum danych lub na innych komputerach lokalnych, możesz to zrobić przy użyciu Azure Stack [.](https://azure.microsoft.com/overview/azure-stack/)

Aby uzyskać więcej informacji na temat publikowania App Service, zobacz:
- [Szybki start — publikowanie w Azure App Service](quickstart-deploy-to-azure.md)
- [Szybki start — publikowanie plików ASP.NET Core systemie Linux.](quickstart-deploy-to-linux.md)
- [Publikowanie aplikacji ASP.NET Core do usługi Azure App Service](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)
- [Rozwiązywanie ASP.NET Core problemów z usługami Azure App Service i IIS.](/aspnet/core/test/troubleshoot-azure-iis)

### <a name="azure-container-registry"></a>Azure Container Registry

[Azure Container Registry](/azure/container-registry/) umożliwia tworzenie i przechowywanie obrazów kontenerów platformy Docker oraz zarządzanie nimi w prywatnym rejestrze dla wszystkich typów wdrożeń kontenerów.

#### <a name="when-to-choose-azure-container-registry"></a>Kiedy należy wybrać Azure Container Registry

- Jeśli masz istniejący potok tworzenia i wdrażania kontenerów platformy Docker.
- Gdy chcesz tworzyć obrazy kontenerów platformy Docker na platformie Azure.

Więcej informacji:

- [Wdrażanie ASP.NET kontenera w rejestrze kontenerów](../containers/hosting-web-apps-in-docker.md)

### <a name="azure-virtual-machine"></a>Maszyna wirtualna platformy Azure

[Usługa Azure Virtual Machines (VMs)](https://azure.microsoft.com/documentation/services/virtual-machines/) umożliwia tworzenie dowolnej liczby zasobów obliczeniowych w chmurze i zarządzanie nimi. Zakładając odpowiedzialność za całe oprogramowanie i aktualizacje na maszyn wirtualnych, możesz dostosować je tak bardzo, jak jest to wymagane przez aplikację. Dostęp do maszyn wirtualnych można uzyskać bezpośrednio za pośrednictwem Pulpit zdalny, a każda z nich będzie utrzymywać przypisany adres IP tak długo, jak to konieczne.

Skalowanie aplikacji hostowanej na maszynach wirtualnych obejmuje zwiększenie dodatkowych maszyn wirtualnych zgodnie z zapotrzebowaniem, a następnie wdrożenie niezbędnego oprogramowania. Ten dodatkowy poziom kontroli umożliwia różne skalowanie w różnych regionach globalnych. Jeśli na przykład aplikacja obsługuje pracowników w różnych biurach regionalnych, możesz skalować maszyny wirtualne zgodnie z liczbą pracowników w tych regionach, co potencjalnie zmniejsza koszty.

Aby uzyskać dodatkowe [](/azure/architecture/guide/technology-choices/compute-decision-tree) informacje, zobacz szczegółowe porównanie usług Azure App Service, Azure Virtual Machines i innych usług platformy Azure, których można użyć jako celu wdrożenia przy użyciu opcji Niestandardowe w usłudze Visual Studio.

#### <a name="when-to-choose-azure-virtual-machines"></a>Kiedy należy wybrać usługę Azure Virtual Machines

- Chcesz wdrożyć aplikację internetową dostępną przez Internet z pełną kontrolą okresu istnienia przypisanych adresów IP.
- Na serwerach potrzebne są dostosowania na poziomie komputera, które obejmują dodatkowe oprogramowanie, takie jak wyspecjalizowany system bazy danych, konkretne konfiguracje sieci, partycje dyskowe itd.
- Potrzebujesz precyzyjnego poziomu kontroli nad skalowaniem aplikacji internetowej.
- Z dowolnej innej przyczyny potrzebujesz bezpośredniego dostępu do serwerów hostowania aplikacji.

> Jeśli chcesz używać usługi Azure Virtual Machines we własnym centrum danych lub na innych komputerach lokalnych, możesz to zrobić przy użyciu Azure Stack [.](https://azure.microsoft.com/overview/azure-stack/)

## <a name="docker-container-registry"></a>Rejestr kontenerów platformy Docker

Jeśli aplikacja korzysta z platformy Docker, możesz opublikować konteneryzowana aplikację w rejestrze kontenerów platformy Docker.

### <a name="when-to-choose-docker-container-registry"></a>Kiedy należy wybrać pozycję Docker Container Registry

- Chcesz wdrożyć konteneryzowana aplikację

Aby uzyskać więcej informacji, zobacz następujące tematy:

- [Wdrażanie ASP.NET kontenera w rejestrze kontenerów](../containers/hosting-web-apps-in-docker.md)
- [Wdrażanie w usłudze Docker Hub](../containers/deploy-docker-hub.md)

## <a name="folder"></a>Folder

Wdrożenie w systemie plików oznacza skopiowanie plików aplikacji do określonego folderu na własnym komputerze. Wdrażanie w folderze jest najczęściej używane do celów testowych lub do wdrażania aplikacji do użycia przez ograniczoną liczbę osób, jeśli na komputerze jest również uruchomiony serwer. Jeśli folder docelowy jest udostępniony w sieci, wdrożenie w systemie plików może udostępnić pliki aplikacji internetowej innym osobom, które mogą następnie wdrożyć je na określonych serwerach.
::: moniker range=">=vs-2019"
Począwszy od Visual Studio 2019 16.8, element docelowy folderu obejmuje możliwość publikowania aplikacji .Net Windows przy użyciu ClickOnce.

Jeśli chcesz opublikować aplikację .NET Core 3.1 lub nowszą, Windows z programem ClickOnce, zobacz [Deploy a .NET Windows application using ClickOnce](quickstart-deploy-using-clickonce-folder.md)(Wdrażanie aplikacji .NET Windows przy użyciu programu ClickOnce ).
::: moniker-end
Wszystkie komputery lokalne z uruchomionym serwerem mogą udostępnić aplikację za pośrednictwem Internetu lub intranetu w zależności od konfiguracji i sieci, z którymi jest połączona. (Jeśli podłączasz komputer bezpośrednio do Internetu, należy szczególnie uważać, aby chronić go przed zewnętrznymi zagrożeniami bezpieczeństwa). Ponieważ zarządzasz tymi maszynami, masz pełną kontrolę nad konfiguracją oprogramowania i sprzętu.

Jeśli z jakiegoś powodu (na przykład dostępu do maszyny) nie możesz korzystać z usług w chmurze, takich jak Azure App Service lub Azure Virtual Machines, możesz użyć Azure Stack [we](https://azure.microsoft.com/overview/azure-stack/) własnym centrum danych. Usługa Azure Stack umożliwia zarządzanie zasobami obliczeniowych i korzystanie z nich za pośrednictwem usług Azure App Service i Azure Virtual Machines przy jednoczesnym zachowaniu wszystkiego w środowisku lokalnym.

### <a name="when-to-choose-file-system-deployment"></a>Kiedy należy wybrać wdrożenie systemu plików

- Aplikację należy wdrożyć tylko w udziałach plików, z których inne osoby będą wdrażać ją na różnych serwerach.
::: moniker range=">=vs-2019"
- Chcesz wdrożyć aplikację .NET Windows przy użyciu ClickOnce
::: moniker-end
- Potrzebujesz tylko lokalnego wdrożenia testowego.
- Chcesz przeanalizować i potencjalnie zmodyfikować pliki aplikacji niezależnie przed wysłaniem ich do innego celu wdrożenia.

Aby uzyskać więcej informacji, zobacz [Szybki start — wdrażanie w folderze lokalnym.](quickstart-deploy-to-local-folder.md)
::: moniker range=">=vs-2019"
Aby uzyskać więcej informacji na temat wdrażania aplikacji .NET Windows przy użyciu programu ClickOnce, zobacz [Deploy a .NET Windows using ClickOnce](quickstart-deploy-using-clickonce-folder.md)(Wdrażanie aplikacji .NET Windows przy użyciu programu ClickOnce).
::: moniker-end

Aby uzyskać dodatkową pomoc przy wybraniu ustawień, zobacz następujące informacje:

- [Wdrożenie zależne od struktury a wdrożenie samodzielne](/dotnet/core/deploying/)
- [Identyfikatory docelowego środowiska uruchomieniowego (przenośne identyfikatory RID i in.)](/dotnet/core/rid-catalog)
- [Konfiguracje debugowania i wydania](../ide/understanding-build-configurations.md)

## <a name="ftpftps-server"></a>Serwer FTP/FTPS

Serwer FTP/FTPS umożliwia wdrożenie aplikacji na serwerze innym niż Platforma Azure. Można go wdrożyć w systemie plików lub dowolnym innym serwerze (internetowym lub intranetowym), do którego masz dostęp, w tym w innych usługach w chmurze. Może współpracować z usługą Web Deploy (plikami lub .ZIP) i protokołem FTP.

Podczas wybierania serwera FTP/FTPS program Visual Studio monit o nazwę profilu, a  następnie zbiera dodatkowe informacje o połączeniu, w tym serwer docelowy lub lokalizację, nazwę lokacji i poświadczenia. Na karcie aplikacji można kontrolować **następujące Ustawienia** zachowania:

- Konfiguracja, którą chcesz wdrożyć.
- Czy usunąć istniejące pliki z miejsca docelowego.
- Określa, czy należy wstępnie skompilować podczas publikowania.
- Czy wykluczyć pliki z App_Data wdrożenia.

W programie można utworzyć dowolną liczbę profilów wdrażania FTP/FTPS Visual Studio, co umożliwia zarządzanie profilami przy użyciu różnych ustawień.

### <a name="when-to-choose-ftpftps-server-deployment"></a>Kiedy należy wybrać wdrożenie serwera FTP/FTPS

- Używasz usług w chmurze u dostawcy innego niż platforma Azure, do którego można uzyskać dostęp za pośrednictwem adresów URL.
- Chcesz wdrożyć przy użyciu poświadczeń innych niż te, które są używane w usłudze Visual Studio, lub te powiązane bezpośrednio z kontami platformy Azure.
- Chcesz usuwać pliki z obiektu docelowego przy każdym wdrożeniu.

## <a name="web-server-iis"></a>Serwer sieci Web (IIS)

Serwer internetowy usług IIS umożliwia wdrożenie aplikacji na serwerze internetowym innym niż Azure. Można ją wdrożyć na serwerze usług IIS (Internet lub Intranet), do którego masz dostęp, w tym na serwerach w innych usługach w chmurze. Może ona współpracować Web Deploy pakietem Web Deploy pakietem.

Podczas wybierania serwera sieci Web usług IIS program Visual Studio monit o nazwę  profilu, a następnie zbiera dodatkowe informacje o połączeniu, w tym serwer docelowy lub lokalizację, nazwę witryny i poświadczenia. Na karcie aplikacji można kontrolować **następujące Ustawienia** zachowania:

- Konfiguracja, którą chcesz wdrożyć.
- Czy usunąć istniejące pliki z miejsca docelowego.
- Określa, czy należy wstępnie skompilować podczas publikowania.
- Czy wykluczyć pliki z App_Data wdrożenia.

W programie można utworzyć dowolną liczbę profilów wdrażania serwera sieci Web usług IIS Visual Studio, co umożliwia zarządzanie profilami przy użyciu różnych ustawień.

### <a name="when-to-choose-web-server-iis-deployment"></a>Kiedy należy wybrać wdrożenie serwera internetowego (IIS)

- Używasz usług IIS do publikowania witryny lub usługi, do której można uzyskać dostęp za pośrednictwem adresów URL.
- Chcesz wdrożyć przy użyciu poświadczeń innych niż te, które są używane w usłudze Visual Studio, lub te powiązane bezpośrednio z kontami platformy Azure.
- Chcesz usuwać pliki z obiektu docelowego przy każdym wdrożeniu.

Aby uzyskać więcej informacji, zobacz [Szybki start — wdrażanie w witrynie internetowej.](quickstart-deploy-to-a-web-site.md)

Aby uzyskać pomoc w rozwiązywaniu problemów z ASP.NET Core usługami IIS, zobacz Troubleshoot ASP.NET Core on Azure App Service and IIS (Rozwiązywanie problemów z Azure App Service [usługami IIS).](/aspnet/core/test/troubleshoot-azure-iis)

## <a name="import-profile"></a>Importowanie profilu

Profil można zaimportować podczas publikowania w usługach IIS lub Azure App Service. Wdrożenie można skonfigurować przy użyciu *pliku ustawień publikowania* (*\* .publishsettings*). Plik ustawień publikowania jest tworzony przez usługę IIS lub Azure App Service lub można go utworzyć ręcznie, a następnie zaimportować do Visual Studio.

Użycie pliku ustawień publikowania może uprościć konfigurację wdrożenia i działa lepiej w środowisku zespołowym niż ręczne konfigurowanie każdego profilu wdrożenia.

### <a name="when-to-choose-import-profile"></a>Kiedy należy wybrać profil importu

- Publikujesz w usługach IIS i chcesz uprościć konfigurację wdrożenia.
- Publikujesz w usługach IIS lub Azure App Service i chcesz przyspieszyć konfigurację wdrożenia do ponownego użycia lub publikowania w tej samej usłudze przez członków zespołu.

Aby uzyskać więcej informacji, zobacz następujące tematy:

- [Importowanie ustawień publikowania i wdrażanie w usługach IIS](tutorial-import-publish-settings-iis.md)
- [Importowanie ustawień publikowania i wdrażanie na platformie Azure](tutorial-import-publish-settings-azure.md)

## <a name="configure-net-deployment-settings"></a>Konfigurowanie ustawień wdrażania .NET

Aby uzyskać dodatkową pomoc przy wybraniu ustawień, zobacz następujące informacje:

- [Wdrożenie zależne od struktury a wdrożenie samodzielne](/dotnet/core/deploying/)
- [Identyfikatory docelowego środowiska uruchomieniowego (przenośne identyfikatory RID i in.)](/dotnet/core/rid-catalog)
- [Konfiguracje debugowania i wydania](../ide/understanding-build-configurations.md)

## <a name="next-steps"></a>Następne kroki

Samouczki:

- [Wdrażanie aplikacji .NET Core za pomocą narzędzia do publikowania](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikowanie podstawowej ASP.NET na platformie Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Wdrożenie w Visual C++](/cpp/windows/deployment-in-visual-cpp)
- [Wdrażanie aplikacji platformy UWP](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikowanie aplikacji Node.js na platformie Azure przy użyciu Web Deploy](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikowanie aplikacji w języku Python w Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
