---
title: Omówienie wdrażania | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "79302001"
---
# <a name="overview-of-deployment-in-visual-studio"></a>Omówienie wdrażania w programie Visual Studio

Wdrażanie aplikacji, usług i składników to rozpowszechnianie ich w celu instalacji na innych komputerach, urządzeniach, serwerach lub w chmurze. W programie Visual Studio możesz wybrać odpowiednią metodę w zależności od typu wdrożenia, jakiego potrzebujesz.

W przypadku wielu typowych typów aplikacji można wdrożyć aplikację bezpośrednio z Eksploratora rozwiązań w programie Visual Studio. Aby uzyskać szybkie spojrzenie na tę funkcję, zobacz [Pierwsze spojrzenie na wdrażanie](../deployment/deploying-applications-services-and-components.md).

![Wybieranie opcji publikowania](../deployment/media/quickstart-publish-azure.png)

## <a name="what-publishing-options-are-right-for-me"></a>Jakie opcje publikowania są dla mnie odpowiednie?

Z poziomu programu Visual Studio aplikacje mogą być publikowane bezpośrednio do następujących obiektów docelowych:

- [Usługa aplikacji platformy Azure](#azure-app-service)
- [Maszyny wirtualne platformy Azure](#azure-virtual-machines)
- [System plików](#file-system)
- [Niestandardowe obiekty docelowe (IIS, FTP itp.),](#custom-targets-iis-ftp)które obejmują wszystkie dowolne serwery sieci Web.

Na karcie **Publikowanie** można wybrać istniejący profil publikowania, zaimportować istniejący lub utworzyć nowy, korzystając z opcji opisanych tutaj. Aby zapoznać się z opcjami publikowania w ide dla różnych typów aplikacji, zobacz [Pierwsze spojrzenie na wdrożenie](../deployment/deploying-applications-services-and-components.md).

## <a name="azure-app-service"></a>Azure App Service

[Usługa Azure App Service](/azure/app-service/app-service-web-overview) i [usługa app service w systemie Linux](/azure/app-service/containers/app-service-linux-intro) pomagają deweloperom szybko tworzyć różne skalowalne aplikacje i usługi sieci Web bez konieczności utrzymywania infrastruktury.

O tym, ile mocy obliczeniowej ma usługa App Service, wybierz [warstwę cenową lub plan](/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview) zawierającej usługę App Service. Możesz mieć wiele aplikacji sieci Web (i innych typów aplikacji) współużytkować tę samą usługę app service bez zmiany warstwy cenowej. Na przykład można hostować tworzenie, przemieszczania i tworzenia aplikacji sieci Web razem w tej samej usłudze App Service.

Usługa app service działa na maszynach wirtualnych hostowanych w chmurze na platformie Azure, ale te maszyny wirtualne są zarządzane dla Ciebie. Każdej aplikacji w usłudze app service \*zostanie przypisany unikatowy adres URL azurewebsites.net; wszystkie warstwy cenowe inne niż Bezpłatne zezwalają na przypisywanie niestandardowych nazw domen do witryny.

### <a name="when-to-choose-azure-app-service"></a>Kiedy wybrać usługę Azure App Service

- Chcesz wdrożyć aplikację sieci web, która jest dostępna za pośrednictwem Internetu.
- Chcesz automatycznie skalować aplikację sieci web zgodnie z zapotrzebowaniem bez konieczności ponownego rozmieszczania.
- Nie chcesz utrzymywać infrastruktury serwera (w tym aktualizacji oprogramowania).
- Nie potrzebujesz żadnych dostosowań na poziomie komputera na serwerach obsługujących aplikację sieci web.

> Jeśli chcesz używać usługi Azure App Service we własnym centrum danych lub na innych komputerach lokalnych, możesz to zrobić za pomocą [usługi Azure Stack.](https://azure.microsoft.com/overview/azure-stack/)

Aby uzyskać więcej informacji na temat publikowania w usłudze App Service, zobacz [Szybki start — publikowanie w usłudze Azure App Service](quickstart-deploy-to-azure.md) i Szybki start — [publikowanie ASP.NET Core w systemie Linux](quickstart-deploy-to-linux.md).

## <a name="azure-virtual-machines"></a>Azure Virtual Machines

[Maszyny wirtualne platformy Azure (VM)](https://azure.microsoft.com/documentation/services/virtual-machines/) umożliwiają tworzenie i zarządzanie dowolną liczbą zasobów obliczeniowych w chmurze. Przyjmując odpowiedzialność za wszystkie oprogramowanie i aktualizacje na maszynach wirtualnych, można dostosować je tak, jak jest to wymagane przez aplikację. Dostęp do maszyn wirtualnych można uzyskać bezpośrednio za pośrednictwem pulpitu zdalnego, a każdy z nich zachowa przypisany adres IP tak długo, jak będzie to pożądane.

Skalowanie aplikacji, która jest hostowana na maszynach wirtualnych, obejmuje rozkręcanie dodatkowych maszyn wirtualnych zgodnie z zapotrzebowaniem, a następnie wdrażanie niezbędnego oprogramowania. Ten dodatkowy poziom kontroli umożliwia różne skalowanie w różnych regionach globalnych. Na przykład jeśli aplikacja obsługuje pracowników w różnych biurach regionalnych, można skalować maszyny wirtualne zgodnie z liczbą pracowników w tych regionach, potencjalnie zmniejszając koszty.

Aby uzyskać dodatkowe informacje, zapoznaj się [ze szczegółowym porównaniem](https://azure.microsoft.com/documentation/articles/choose-web-site-cloud-service-vm/) usługi Azure App Service, maszyn wirtualnych platformy Azure i innych usług platformy Azure, których można użyć jako obiektu docelowego wdrożenia przy użyciu opcji niestandardowej w programie Visual Studio.

### <a name="when-to-choose-azure-app-virtual-machines"></a>Kiedy wybrać maszyny wirtualne aplikacji platformy Azure

- Chcesz wdrożyć aplikację sieci web, która jest dostępna za pośrednictwem Internetu, z pełną kontrolą nad okresem istnienia przypisanych adresów IP.
- Potrzebne są dostosowania na poziomie komputera na serwerach, które obejmują dodatkowe oprogramowanie, takie jak wyspecjalizowany system baz danych, określone konfiguracje sieci, partycje dysków i tak dalej.
- Chcesz uzyskać odpowiedni poziom kontroli nad skalowaniem aplikacji sieci web.
- Potrzebujesz bezpośredniego dostępu do serwerów hostujących twoją aplikację z jakiegokolwiek innego powodu.

> Jeśli chcesz używać maszyn wirtualnych platformy Azure we własnym centrum danych lub na innych komputerach lokalnych, możesz to zrobić za pomocą [usługi Azure Stack.](https://azure.microsoft.com/overview/azure-stack/)

## <a name="file-system"></a>System plików

Wdrożenie w systemie plików oznacza po prostu skopiowanie plików aplikacji do określonego folderu na własnym komputerze. Jest to najczęściej używane do celów testowych lub do wdrażania aplikacji do użytku przez ograniczoną liczbę osób, jeśli na komputerze jest również uruchomiony serwer. Jeśli folder docelowy jest udostępniany w sieci, wdrożenie w systemie plików może udostępnić pliki aplikacji sieci web innym osobom, które mogą je następnie wdrożyć na określonych serwerach.

Wszystkie komputery lokalne z serwerem mogą udostępniać aplikację za pośrednictwem Internetu lub intranetu w zależności od konfiguracji i sieci, z którymi jest nawiązycona. (Jeśli komputer jest połączony bezpośrednio z Internetem, należy zachować szczególną ostrożność, aby chronić go przed zewnętrznymi zagrożeniami bezpieczeństwa). Ponieważ zarządzasz tymi komputerami, masz pełną kontrolę nad konfiguracjami oprogramowania i sprzętu.

Należy zauważyć, że jeśli z jakiegokolwiek powodu (na przykład dostęp do komputera) nie można korzystać z usług w chmurze, takich jak usługa Azure App Service lub maszyny wirtualne platformy Azure, można użyć [usługi Azure Stack](https://azure.microsoft.com/overview/azure-stack/) we własnym centrum danych. Usługa Azure Stack umożliwia zarządzanie zasobami obliczeniowymi i korzystanie z niego za pośrednictwem usługi Azure App Service i maszyn wirtualnych platformy Azure, a jednocześnie zapewnia wszystko w środowisku lokalnym.

### <a name="when-to-choose-file-system-deployment"></a>Kiedy wybrać wdrożenie systemu plików

- Wystarczy wdrożyć aplikację do udziału plików, z którego inni będą wdrażać go na różnych serwerach.
- Potrzebne jest tylko wdrożenie testu lokalnego.
- Chcesz zbadać i potencjalnie zmodyfikować pliki aplikacji niezależnie przed wysłaniem ich do innego miejsca docelowego wdrożenia.

Aby uzyskać więcej informacji, zobacz [Szybki start — wdrażanie w folderze lokalnym](quickstart-deploy-to-local-folder.md)

## <a name="custom-targets-iis-ftp"></a>Obiekty docelowe (IIS, FTP)

Niestandardowy obiekt docelowy umożliwia wdrożenie aplikacji do obiektu docelowego innego niż usługa Azure App Service, maszyny wirtualne platformy Azure lub lokalny system plików. Można go wdrożyć w systemie plików lub na dowolnym innym serwerze (Internetowym lub Intranet), do którego masz dostęp, w tym w innych usługach w chmurze. Może pracować z wdrażaniem w sieci Web (pliki lub . ZIP) i FTP.

Wybierając niestandardowy obiekt docelowy, program Visual Studio monituje o nazwę profilu, a następnie zbiera dodatkowe informacje **o połączeniu,** w tym serwer docelowy lub lokalizację, nazwę witryny i poświadczenia. Na karcie **Ustawienia** można kontrolować następujące zachowania:

- Konfiguracja, którą chcesz wdrożyć.
- Czy usunąć istniejące pliki z miejsca docelowego.
- Czy wstępnie skompilować podczas publikowania.
- Określa, czy pliki w folderze App_Data mają być wykluczone z wdrożenia.

Można utworzyć dowolną liczbę profilów wdrażania niestandardowego w programie Visual Studio, dzięki czemu można zarządzać profilami z różnymi ustawieniami.

### <a name="when-to-choose-custom-deployment"></a>Kiedy wybrać wdrożenie niestandardowe

- Używasz usług w chmurze na dostawcy innego niż Azure, które są dostępne za pośrednictwem adresów URL.
- Chcesz wdrożyć przy użyciu poświadczeń innych niż te, które są używane w programie Visual Studio lub te powiązane bezpośrednio z kontami platformy Azure.
- Chcesz usunąć pliki z obiektu docelowego przy każdym wdrożeniu.

Aby uzyskać więcej informacji, zobacz [Szybki start — wdrażanie w witrynie sieci Web](quickstart-deploy-to-a-web-site.md)

## <a name="next-steps"></a>Następne kroki

Samouczki:

- [Wdrażanie aplikacji .NET Core za pomocą narzędzia publikowania](/dotnet/core/deploying/deploy-with-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikowanie ASP.NET podstawowej aplikacji na platformie Azure](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Wdrażanie w języku Visual C++](/cpp/windows/deployment-in-visual-cpp)
- [Wdrażanie aplikacji platformy uniwersalnej systemu Windows](/windows/uwp/packaging/packaging-uwp-apps?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikowanie aplikacji Node.js na platformie Azure przy użyciu narzędzia Web Deploy](https://github.com/Microsoft/nodejstools/wiki/Publish-to-Azure-Website-using-Web-Deploy?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
- [Publikowanie aplikacji języka Python w usłudze Azure App Service](../python/publishing-python-web-applications-to-azure-from-visual-studio.md?toc=/visualstudio/deployment/toc.json&bc=/visualstudio/deployment/_breadcrumb/toc.json)
