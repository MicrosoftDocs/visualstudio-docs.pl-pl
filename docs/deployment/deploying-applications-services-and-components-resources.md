---
title: Wdrażanie aplikacji Visual Studio w folderze, usługach IIS, na platformie Azure lub w innym miejscu docelowym
description: Dowiedz się więcej o opcjach publikowania aplikacji za pomocą Kreatora publikacji
ms.custom: contperfq1
ms.date: 08/21/2020
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
ms.openlocfilehash: cccba4c299d5b12bdc00666a0b00f073fba12278
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "90036699"
---
# <a name="deploy-your-app-to-a-folder-iis-azure-or-another-destination"></a>Wdrażanie aplikacji w folderze, usługach IIS, na platformie Azure lub w innym miejscu docelowym

Wdrażanie aplikacji, usług i składników to rozpowszechnianie ich w celu instalacji na innych komputerach, urządzeniach, serwerach lub w chmurze. W programie Visual Studio możesz wybrać odpowiednią metodę w zależności od typu wdrożenia, jakiego potrzebujesz.

Uzyskaj pomoc dotyczącą zadania wdrożenia:

- Nie masz pewności co do wyboru opcji wdrażania? Zobacz, [jakie opcje publikowania są odpowiednie dla mnie?](#what-publishing-options-are-right-for-me)
- Aby uzyskać pomoc dotyczącą problemów z wdrażaniem Azure App Service lub IIS, zobacz [Rozwiązywanie problemów ASP.NET Core na Azure App Service i usługach IIS](/aspnet/core/test/troubleshoot-azure-iis).
- Aby uzyskać pomoc dotyczącą konfigurowania ustawień wdrożenia platformy .NET, zobacz [Konfigurowanie ustawień wdrożenia platformy .NET](#configure-net-deployment-settings).
- Aby wdrożyć w nowym miejscu docelowym, jeśli wcześniej utworzono profil publikowania, wybierz opcję **Nowy** z okna **publikowania** dla skonfigurowanego profilu.

   ![Utwórz nowy profil publikowania](../deployment/media/create-a-new-publish-profile.png)

   Następnie wybierz opcję wdrożenia w oknie publikowanie. Aby uzyskać informacje na temat opcji publikowania, zobacz następujące sekcje.

## <a name="what-publishing-options-are-right-for-me"></a>Jakie opcje publikowania są odpowiednie dla mnie?

W programie Visual Studio aplikacje można publikować bezpośrednio w następujących celach:

::: moniker range=">=vs-2019"
- [Azure](#azure)
- [Container Registry platformy Docker](#docker-container-registry)
- [Folder](#folder)
- [Serwer FTP/FTPS](#ftpftps-server)
- [Serwer sieci Web (IIS)](#web-server-iis)
- [Importuj profil](#import-profile)
::: moniker-end
::: moniker range="vs-2017"
- [App Service](#azure-app-service)
- [App Service dla systemu Linux](#azure-app-service)
- [Usługi IIS (Wybierz usługi IIS, FTP itp.)](#web-server-iis)
- [FTP/FTPS (Wybierz usługi IIS, FTP itp.)](#ftpftps-server)
- [Folder](#folder)
- [Importuj profil](#import-profile)
::: moniker-end

Powyższe opcje są wyświetlane jak pokazano na poniższej ilustracji podczas tworzenia nowego profilu publikowania.

::: moniker range=">=vs-2019"
![Wybierz opcję publikowania](../deployment/media/quickstart-publish-dialog.png)
::: moniker-end
::: moniker range="vs-2017"
![Wybierz opcję publikowania](../deployment/media/quickstart-publish-dialog-vs-2017.png)
::: moniker-end

Aby zapoznać się z bardziej ogólnymi opcjami wdrażania aplikacji, zobacz [pierwsze spojrzenie na wdrożenie](../deployment/deploying-applications-services-and-components.md).

## <a name="azure"></a>Azure 

Po wybraniu platformy Azure Możesz wybrać jedną z opcji:

- [Azure App Service](#azure-app-service) uruchomiony w systemie Windows, Linux lub w postaci obrazu platformy Docker
- Obraz platformy Docker wdrożony w [Azure Container Registry](#azure-container-registry)
- [Maszyna wirtualna platformy Azure](#azure-virtual-machine)

![Wybierz usługę platformy Azure](../deployment/media/quickstart-choose-azure-service.png)

### <a name="azure-app-service"></a>Azure App Service

[Azure App Service](/azure/app-service/app-service-web-overview) ułatwia deweloperom szybkie tworzenie skalowalnych aplikacji sieci Web i usług bez konieczności utrzymywania infrastruktury. App Service działa na maszynach wirtualnych hostowanych w chmurze na platformie Azure, ale te maszyny wirtualne są zarządzane przez Ciebie. Dla każdej aplikacji w App Service zostanie przypisany unikatowy \* adres URL. azurewebsites.NET; wszystkie warstwy cenowe inne niż bezpłatna umożliwiają przypisanie niestandardowych nazw domen do lokacji.

Należy określić, ile mocy obliczeniowej ma App Service, wybierając [warstwę cenową lub plan](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) dla App Service zawierającej. Można mieć wiele aplikacji sieci Web (i innych typów aplikacji), które współużytkują tę samą App Service bez zmiany warstwy cenowej. Na przykład możesz hostować aplikacje sieci Web do tworzenia, przemieszczania i produkcji w tym samym App Service.

#### <a name="when-to-choose-azure-app-service"></a>Kiedy należy wybrać Azure App Service

- Chcesz wdrożyć aplikację sieci Web, która jest dostępna za pomocą Internetu.
- Chcesz automatycznie skalować aplikację sieci Web zgodnie z zapotrzebowaniem bez konieczności ponownego wdrażania.
- Nie chcesz zachować infrastruktury serwera (w tym aktualizacji oprogramowania).
- Na serwerach, na których jest hostowana aplikacja sieci Web, nie są wymagane żadne dostosowania na poziomie komputera.

> Jeśli chcesz używać Azure App Service we własnym centrum danych lub na innych komputerach lokalnych, możesz to zrobić przy użyciu [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

Aby uzyskać więcej informacji o publikowaniu do App Service, zobacz:
- [Szybki Start — publikowanie do Azure App Service](quickstart-deploy-to-azure.md)
- [Szybki Start — publikowanie ASP.NET Core w systemie Linux](quickstart-deploy-to-linux.md).
- [Publikowanie aplikacji ASP.NET Core w Azure App Service](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs)
- [Rozwiązywanie problemów ASP.NET Core na Azure App Service i usługach IIS](/aspnet/core/test/troubleshoot-azure-iis).

### <a name="azure-container-registry"></a>Azure Container Registry

[Azure Container Registry](/azure/container-registry/) umożliwia tworzenie i przechowywanie obrazów kontenerów platformy Docker i artefaktów oraz zarządzanie nimi w rejestrze prywatnym dla wszystkich typów wdrożeń kontenerów.

#### <a name="when-to-choose-azure-container-registry"></a>Kiedy należy wybrać Azure Container Registry

- Gdy masz istniejący potok platformy Docker do tworzenia i wdrażania kontenerów.
- Gdy chcesz tworzyć obrazy kontenerów platformy Docker na platformie Azure.

Więcej informacji:

- [Wdrażanie kontenera ASP.NET do rejestru kontenerów](../containers/hosting-web-apps-in-docker.md)

### <a name="azure-virtual-machine"></a>Maszyna wirtualna platformy Azure

[Usługa Azure Virtual Machines (maszyny wirtualne)](https://azure.microsoft.com/documentation/services/virtual-machines/) umożliwia tworzenie dowolnej liczby zasobów obliczeniowych w chmurze i zarządzanie nią. Przy założeniu, że odpowiedzialność za wszystkie oprogramowanie i aktualizacje na maszynach wirtualnych, można dostosować je tak długo, jak jest to wymagane przez aplikację. Dostęp do maszyn wirtualnych można uzyskać bezpośrednio za pomocą Pulpit zdalny, a każda z nich będzie obsługiwać przypisany adres IP, tak długo, jak to konieczne.

Skalowanie aplikacji hostowanej na maszynach wirtualnych obejmuje rozmieszczenie dodatkowych maszyn wirtualnych zgodnie z zapotrzebowaniem, a następnie wdrożenie niezbędnego oprogramowania. Ten dodatkowy poziom kontroli umożliwia skalowanie w różny sposób w różnych regionach globalnych. Na przykład jeśli aplikacja obsługuje pracowników w różnych biurach regionalnych, można skalować maszyny wirtualne zgodnie z liczbą pracowników w tych regionach, co może powodować obniżenie kosztów.

Dodatkowe informacje znajdują się w [szczegółowym porównaniu](/azure/architecture/guide/technology-choices/compute-decision-tree) między Azure App Service, Azure Virtual Machines i innymi usługami platformy Azure, których można użyć jako celu wdrożenia przy użyciu opcji niestandardowej w programie Visual Studio.

#### <a name="when-to-choose-azure-virtual-machines"></a>Kiedy należy wybrać platformę Azure Virtual Machines

- Chcesz wdrożyć aplikację sieci Web, która jest dostępna za pośrednictwem Internetu, z pełną kontrolą nad okresem istnienia przypisanych adresów IP.
- Na serwerach programu wymagane są dostosowania na poziomie komputera, w tym dodatkowe oprogramowanie, takie jak wyspecjalizowany system bazy danych, konkretne konfiguracje sieci, partycje dysku i tak dalej.
- Chcesz mieć precyzyjną kontrolę nad skalowaniem aplikacji sieci Web.
- Potrzebujesz bezpośredniego dostępu do serwerów obsługujących aplikację z dowolnego innego powodu.

> Jeśli chcesz korzystać z usługi Azure Virtual Machines we własnym centrum danych lub na innych komputerach lokalnych, możesz to zrobić przy użyciu [Azure Stack](https://azure.microsoft.com/overview/azure-stack/).

## <a name="docker-container-registry"></a>Rejestr kontenerów platformy Docker

Jeśli aplikacja korzysta z platformy Docker, można opublikować aplikację z kontenerów w rejestrze kontenerów platformy Docker.

### <a name="when-to-choose-docker-container-registry"></a>Kiedy należy wybrać Container Registry platformy Docker

- Chcesz wdrożyć aplikację mającą kontener

Aby uzyskać więcej informacji, zobacz następujące tematy:

- [Wdrażanie kontenera ASP.NET do rejestru kontenerów](../containers/hosting-web-apps-in-docker.md)
- [Wdrażanie w usłudze Docker Hub](../containers/deploy-docker-hub.md)

## <a name="folder"></a>Folder

Wdrożenie w systemie plików oznacza, że wystarczy skopiować pliki aplikacji do określonego folderu na swoim komputerze. Jest to najczęściej używane do celów testowych lub do wdrożenia aplikacji do użytku przez ograniczoną liczbę osób, jeśli na komputerze jest również uruchomiony serwer. Jeśli folder docelowy jest udostępniony w sieci, wdrożenie w systemie plików może udostępnić pliki aplikacji sieci Web innym użytkownikom, którzy mogą następnie wdrożyć ją na określonych serwerach.

Wszystkie maszyny lokalne, na których działa serwer, mogą udostępnić aplikację za pośrednictwem Internetu lub intranetu w zależności od konfiguracji i sieci, z którymi są połączone. (Jeśli komputer zostanie połączony bezpośrednio z Internetem, należy szczególnie uważnie chronić go przed zagrożeniami bezpieczeństwa zewnętrznego). Ponieważ zarządzasz tymi maszynami, masz pełną kontrolę nad konfiguracjami oprogramowania i sprzętu.

Należy pamiętać, że jeśli z jakiegokolwiek powodu (na przykład dostęp do komputera) nie można korzystać z usług w chmurze, takich jak Azure App Service lub Azure Virtual Machines, można użyć [Azure Stack](https://azure.microsoft.com/overview/azure-stack/) we własnym centrum danych. Azure Stack pozwala zarządzać zasobami obliczeniowymi i korzystać z nich za pomocą Azure App Service i Virtual Machines platformy Azure, jednocześnie zachowując wszystkie dane lokalne.

### <a name="when-to-choose-file-system-deployment"></a>Kiedy należy wybrać wdrożenie systemu plików

- Aplikację należy wdrożyć tylko w udziale plików, z którego inne będą wdrażać je na różnych serwerach.
- Wymagane jest tylko lokalne wdrożenie testowe.
- Chcesz przeanalizować i potencjalnie zmodyfikować pliki aplikacji niezależnie przed ich wysłaniem do innego celu wdrożenia.

Aby uzyskać więcej informacji, zobacz [Szybki Start-Deploy do folderu lokalnego](quickstart-deploy-to-local-folder.md).

Aby uzyskać dodatkową pomoc dotyczącą wybierania ustawień, zobacz następujące tematy:

- [Wdrażanie zależne od platformy a wdrożenie samodzielne](/dotnet/core/deploying/)
- [Docelowe identyfikatory środowiska uruchomieniowego (Portable RID, et al)](/dotnet/core/rid-catalog)
- [Konfiguracje debugowania i wydania](../ide/understanding-build-configurations.md)

## <a name="ftpftps-server"></a>Serwer FTP/FTPS

Serwer FTP/FTPS umożliwia wdrożenie aplikacji na serwerze innym niż Azure. Można ją wdrożyć w systemie plików lub na dowolnym innym serwerze (Internet lub intranecie), do którego masz dostęp, w tym także w innych usługach w chmurze. Może współpracować z programem Web Deploy (pliki lub. ZIP) i FTP.

W przypadku wybrania serwera FTP/FTPS program Visual Studio poprosi o podanie nazwy profilu, a następnie zbiera dodatkowe informacje o **połączeniu** , w tym serwer docelowy lub lokalizację, nazwę lokacji i poświadczenia. Na karcie **Ustawienia** można kontrolować następujące zachowania:

- Konfiguracja, którą chcesz wdrożyć.
- Czy usunąć istniejące pliki z lokalizacji docelowej.
- Czy należy prekompilować podczas publikowania.
- Określa, czy pliki w folderze App_Data mają być wykluczone z wdrożenia.

W programie Visual Studio można utworzyć dowolną liczbę profilów wdrażania FTP/FTPS, co umożliwia zarządzanie profilami przy użyciu różnych ustawień.

### <a name="when-to-choose-ftpftps-server-deployment"></a>Kiedy należy wybrać wdrożenie serwera FTP/FTPS

- Używasz usług w chmurze na dostawcy innym niż Azure, do którego można uzyskać dostęp za pośrednictwem adresów URL.
- Chcesz wdrożyć przy użyciu poświadczeń innych niż te, które są używane w programie Visual Studio, lub powiązane bezpośrednio z kontami platformy Azure.
- Chcesz usunąć pliki z obiektu docelowego przy każdym wdrożeniu.

## <a name="web-server-iis"></a>Serwer sieci Web (IIS)

Serwer sieci Web usług IIS umożliwia wdrożenie aplikacji na serwerze sieci Web innym niż Azure. Można ją wdrożyć na serwerze usług IIS (Internet lub intranecie), do którego masz dostęp, w tym także w innych usługach w chmurze. Może współpracować z Web Deploy lub pakietem Web Deploy.

W przypadku wybrania serwera sieci Web usług IIS program Visual Studio poprosi o podanie nazwy profilu, a następnie zbiera dodatkowe informacje o **połączeniu** , w tym serwer docelowy lub lokalizację, nazwę lokacji i poświadczenia. Na karcie **Ustawienia** można kontrolować następujące zachowania:

- Konfiguracja, którą chcesz wdrożyć.
- Czy usunąć istniejące pliki z lokalizacji docelowej.
- Czy należy prekompilować podczas publikowania.
- Określa, czy pliki w folderze App_Data mają być wykluczone z wdrożenia.

W programie Visual Studio można utworzyć dowolną liczbę profilów wdrażania serwera sieci Web usług IIS, dzięki czemu możliwe jest zarządzanie profilami przy użyciu różnych ustawień.

### <a name="when-to-choose-web-server-iis-deployment"></a>Kiedy należy wybrać wdrożenie serwera sieci Web (IIS)

- Używasz usług IIS do publikowania witryny lub usługi, do której można uzyskać dostęp za pośrednictwem adresów URL.
- Chcesz wdrożyć przy użyciu poświadczeń innych niż te, które są używane w programie Visual Studio, lub powiązane bezpośrednio z kontami platformy Azure.
- Chcesz usunąć pliki z obiektu docelowego przy każdym wdrożeniu.

Aby uzyskać więcej informacji, zobacz [Przewodnik Szybki Start — wdrażanie w witrynie sieci Web](quickstart-deploy-to-a-web-site.md).

Aby uzyskać pomoc w rozwiązywaniu problemów ASP.NET Core w usługach IIS, zobacz [Rozwiązywanie problemów ASP.NET Core na Azure App Service i usługach IIS](/aspnet/core/test/troubleshoot-azure-iis).

## <a name="import-profile"></a>Importuj profil

Możesz zaimportować profil podczas publikowania w usługach IIS lub Azure App Service. Wdrożenie można skonfigurować przy użyciu *pliku ustawień publikowania* (* \* . publishsettings*). Plik ustawień publikowania jest tworzony przez usługi IIS lub Azure App Service lub można go utworzyć ręcznie, a następnie można go zaimportować do programu Visual Studio.

Użycie pliku ustawień publikowania może uprościć konfigurację wdrożenia i działać lepiej w środowisku zespołu, a jednocześnie ręcznie skonfigurować każdy profil wdrożenia.

### <a name="when-to-choose-import-profile"></a>Po wybraniu opcji Importuj profil

- Publikujesz w usługach IIS i chcesz uprościć konfigurację wdrożenia.
- Publikujesz w usługach IIS lub Azure App Service i chcesz przyspieszyć konfigurację wdrożenia w celu ponownego użycia lub dla członków zespołu publikowanych w tej samej usłudze.

Aby uzyskać więcej informacji, zobacz następujące tematy:

- [Importowanie ustawień publikowania i wdrażanie w usługach IIS](tutorial-import-publish-settings-iis.md)
- [Importowanie ustawień publikowania i wdrażanie na platformie Azure](tutorial-import-publish-settings-azure.md)

## <a name="configure-net-deployment-settings"></a>Konfigurowanie ustawień wdrożenia platformy .NET

Aby uzyskać dodatkową pomoc dotyczącą wybierania ustawień, zobacz następujące tematy:

- [Wdrażanie zależne od platformy a wdrożenie samodzielne](/dotnet/core/deploying/)
- [Docelowe identyfikatory środowiska uruchomieniowego (Portable RID, et al)](/dotnet/core/rid-catalog)
- [Konfiguracje debugowania i wydania](../ide/understanding-build-configurations.md)

## <a name="next-steps"></a>Następne kroki

Samouczki:

- [Wdrażanie aplikacji .NET Core za pomocą narzędzia do publikowania](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikowanie aplikacji ASP.NET Core na platformie Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Wdrożenie w Visual C++](/cpp/windows/deployment-in-visual-cpp)
- [Wdrażanie aplikacji platformy UWP](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikowanie aplikacji Node.js na platformie Azure przy użyciu usługi Web Deploy](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikowanie aplikacji w języku Python w celu Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)