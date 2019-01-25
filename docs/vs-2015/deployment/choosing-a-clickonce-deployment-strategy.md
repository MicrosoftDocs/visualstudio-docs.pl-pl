---
title: Wybieranie strategii wdrażania ClickOnce | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, strategies
- deploying applications, ClickOnce
ms.assetid: 98bcab65-ab8b-4ed1-9adc-fdacf92b8106
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 619d70b79d75cc45add0d541cd081d9ac0f258d5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54774041"
---
# <a name="choosing-a-clickonce-deployment-strategy"></a>Wybieranie strategii wdrażania ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Istnieją trzy różne strategie wdrażania [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji, a wybrana strategia zależy głównie od typu aplikacji, w której przeprowadzasz wdrożenie. Poniżej przedstawiono wszystkie trzy strategie wdrażania:  
  
-   Instalacja z sieci Web lub udziału sieciowego  
  
-   Instalacja z dysku CD  
  
-   Uruchamianie aplikacji z sieci Web lub udziału sieciowego  
  
    > [!NOTE]
    >  Oprócz wybrania strategii wdrażania, warto również wybrać strategię dostarczania aktualizacji aplikacji. Aby uzyskać więcej informacji, zobacz [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
## <a name="install-from-the-web-or-a-network-share"></a>Instalacja z sieci Web lub udziału sieciowego  
 Gdy jest używana ta strategia, aplikacja jest wdrażana na serwerze sieci Web lub w sieciowym udziale plików. Gdy użytkownik końcowy chce zainstalować aplikację, klika ikonę na stronie sieci Web lub klika dwukrotnie ikonę w udziale plików. Aplikacja jest następnie pobierana, instalowana i uruchamiana na komputerze użytkownika końcowego. Elementy są dodawane do **Start** menu i **apletu Dodaj lub usuń programy** w **Panelu sterowania**.  
  
 Ta strategia jest zależna od połączeń sieciowych, więc sprawdza się najlepiej w przypadku aplikacji, które zostaną wdrożone dla użytkowników mających dostęp do sieci lokalnej lub szybkiego połączenia z Internetem.  
  
 W przypadku wdrażania aplikacji z sieci Web można przekazać argumenty do aplikacji podczas aktywowania jej za pomocą adresu URL. Aby uzyskać więcej informacji, zobacz [jak: Pobieranie informacji o ciągu zapytania w aplikacji ClickOnce w trybie Online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md). Nie można przekazywać argumentów do aplikacji, która jest aktywowana za pomocą jednej z pozostałych metod opisanych w tym dokumencie.  
  
 Aby włączyć tę strategię wdrażania w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], kliknij przycisk **z sieci Web** lub **z UNC udziału pliku lub ścieżki** na **sposób instalacji** strony w Kreatorze publikacji.  
  
 Jest to domyślna strategia wdrażania.  
  
## <a name="install-from-a-cd"></a>Instalacja z dysku CD  
 Gdy jest używana ta strategia, aplikacja jest wdrażana na nośniku wymiennym, takim jak dysk CD-ROM lub DVD. Podobnie jak w przypadku poprzedniej opcji, gdy użytkownik zachce zainstalować aplikację, zostanie ona zainstalowana i uruchomiona, i elementy są dodawane do **Start** menu i **apletu Dodaj lub usuń programy** w **kontroli Panel**.  
  
 Ta strategia sprawdza się najlepiej w przypadku aplikacji wdrażanej dla użytkowników, którzy nie mają stałej łączności sieciowej lub używają połączeń o niskiej przepustowości. Aplikacja jest instalowana z nośnika wymiennego, więc do instalacji nie jest potrzebne połączenie sieciowe, jednak łączność sieciowa jest potrzebna do pobierania aktualizacji aplikacji.  
  
 Aby włączyć tę strategię wdrażania w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], kliknij przycisk **z dysku CD-ROM lub DVD-ROM** na **sposób instalacji** strony w Kreatorze publikacji.  
  
 Aby ręcznie włączyć tę strategię wdrażania, zmienić **deploymentProvider** tag w manifeście wdrożenia. (W programie Visual Studio, ta właściwość jest uwidaczniana jako **adres URL instalacji** na **Publikuj** strony w Projektancie projektu. W programie Mage.exe jest **lokalizacja początkowa**.)  
  
## <a name="start-the-application-from-the-web-or-a-network-share"></a>Uruchamianie aplikacji z sieci Web lub udziału sieciowego  
 Ta strategia jest podobna do pierwszej, z tym że aplikacja zachowuje się jak aplikacja internetowa. Gdy użytkownik kliknie łącze na stronie sieci Web (lub kliknie dwukrotnie ikonę w udziale plików), aplikacja jest uruchamiana. Gdy użytkownicy zamykają aplikację, nie jest już dostępny na swoim komputerze lokalnym; nic nie zostanie dodany do **Start** menu lub **apletu Dodaj lub usuń programy** w **Panelu sterowania**.  
  
> [!NOTE]
>  Technicznie aplikacja jest pobierana i instalowana w pamięci podręcznej aplikacji na komputerze lokalnym, tak samo jak aplikacja internetowa jest pobierana do internetowej pamięci podręcznej. Podobnie jak w przypadku pamięci podręcznej sieci Web, pliki są na końcu usuwane z pamięci podręcznej aplikacji. Jednak z punktu widzenia użytkownika aplikacja jest uruchamiana z sieci Web lub udziału plików.  
  
 Ta strategia najlepiej sprawdza się w przypadku aplikacji, które są rzadko używane, takich jak na przykład narzędzie do obliczania nagród dla pracowników, które zazwyczaj jest używane raz do roku.  
  
 Aby włączyć tę strategię wdrażania w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], kliknij przycisk **nie należy instalować aplikację** na **instalacji lub uruchom z sieci Web** strony w Kreatorze publikacji.  
  
 Aby ręcznie włączyć tę strategię wdrażania, zmienić **zainstalować** tag w manifeście wdrożenia. (Jego wartość może być **true** lub **false**. W programie Mage.exe, użyj **tylko Online** opcji **typ aplikacji** listy.)  
  
## <a name="web-browser-support"></a>Obsługa przeglądarek sieci Web  
 Aplikacje, których platformą docelową jest program .NET Framework 3.5, można zainstalować przy użyciu dowolnej przeglądarki.  
  
 Aplikacje, których platformą docelową jest program .NET Framework 2.0, wymagają programu Internet Explorer.  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażania i zabezpieczeń ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Instrukcje: Publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)
