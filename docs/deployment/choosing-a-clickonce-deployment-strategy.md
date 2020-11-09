---
title: Wybieranie strategii wdrażania ClickOnce | Microsoft Docs
description: Zapoznaj się z strategiami wdrażania aplikacji ClickOnce i sposobami wybierania strategii w zależności od typu wdrażanej aplikacji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, strategies
- deploying applications, ClickOnce
ms.assetid: 98bcab65-ab8b-4ed1-9adc-fdacf92b8106
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d623c47960a3c1a44c184df52488682659d5238d
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383173"
---
# <a name="choose-a-clickonce-deployment-strategy"></a>Wybieranie strategii wdrażania technologii ClickOnce
Istnieją trzy różne strategie wdrażania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. wybrana strategia zależy głównie od typu wdrażanej aplikacji. Poniżej przedstawiono wszystkie trzy strategie wdrażania:

- Instalacja z sieci Web lub udziału sieciowego

- Instalacja z dysku CD

- Uruchamianie aplikacji z sieci Web lub udziału sieciowego

    > [!NOTE]
    > Oprócz wybrania strategii wdrażania, warto również wybrać strategię dostarczania aktualizacji aplikacji. Aby uzyskać więcej informacji, zobacz [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

## <a name="install-from-the-web-or-a-network-share"></a>Instalowanie z sieci Web lub udziału sieciowego
 Gdy jest używana ta strategia, aplikacja jest wdrażana na serwerze sieci Web lub w sieciowym udziale plików. Gdy użytkownik końcowy chce zainstalować aplikację, klika ikonę na stronie sieci Web lub klika dwukrotnie ikonę w udziale plików. Aplikacja jest następnie pobierana, instalowana i uruchamiana na komputerze użytkownika końcowego. Elementy są dodawane do menu **Start** i **Dodaj lub usuń programy** w **Panelu sterowania**.

 Ta strategia jest zależna od połączeń sieciowych, więc sprawdza się najlepiej w przypadku aplikacji, które zostaną wdrożone dla użytkowników mających dostęp do sieci lokalnej lub szybkiego połączenia z Internetem.

 W przypadku wdrażania aplikacji z sieci Web można przekazać argumenty do aplikacji podczas aktywowania jej za pomocą adresu URL. Aby uzyskać więcej informacji, zobacz [How to: pobieranie informacji o ciągu zapytania w aplikacji ClickOnce w trybie online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md). Nie można przekazywać argumentów do aplikacji, która jest aktywowana za pomocą jednej z pozostałych metod opisanych w tym dokumencie.

 Aby włączyć tę strategię wdrażania w programie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , kliknij opcję **z sieci Web** lub **ze ścieżki UNC lub udziału plików** na stronie **jak zainstalowane** w Kreatorze publikacji.

 Jest to domyślna strategia wdrażania.

## <a name="start-the-application-from-the-web-or-a-network-share"></a>Uruchamianie aplikacji z sieci Web lub udziału sieciowego
 Ta strategia jest podobna do pierwszej, z tym że aplikacja zachowuje się jak aplikacja internetowa. Gdy użytkownik kliknie łącze na stronie sieci Web (lub kliknie dwukrotnie ikonę w udziale plików), aplikacja jest uruchamiana. Gdy użytkownik zamknie aplikację, nie jest już dostępna na komputerze lokalnym; nic nie zostało dodane do menu **Start** lub **Dodaj lub usuń programy** w **Panelu sterowania**.

> [!NOTE]
> Technicznie aplikacja jest pobierana i instalowana w pamięci podręcznej aplikacji na komputerze lokalnym, tak samo jak aplikacja internetowa jest pobierana do internetowej pamięci podręcznej. Podobnie jak w przypadku pamięci podręcznej sieci Web, pliki są na końcu usuwane z pamięci podręcznej aplikacji. Jednak z punktu widzenia użytkownika aplikacja jest uruchamiana z sieci Web lub udziału plików.

 Ta strategia najlepiej sprawdza się w przypadku aplikacji, które są rzadko używane, takich jak na przykład narzędzie do obliczania nagród dla pracowników, które zazwyczaj jest używane raz do roku.

 Aby włączyć tę strategię wdrażania w programie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , kliknij pozycję nie **Instaluj aplikacji** na stronie **Instalowanie lub uruchamianie z sieci Web** Kreatora publikacji.

 Aby włączyć tę strategię wdrażania ręcznie, należy zmienić tag **instalacji** w manifeście wdrożenia. (Jego wartość może być **równa true** lub **false**. W *Mage.exe* Użyj opcji **tylko online** na liście **Typ aplikacji** ).

## <a name="install-from-a-cd"></a>Instalacja z dysku CD
 Gdy jest używana ta strategia, aplikacja jest wdrażana na nośniku wymiennym, takim jak dysk CD-ROM lub DVD. Podobnie jak w przypadku poprzedniej opcji, gdy użytkownik zdecyduje się na zainstalowanie aplikacji, zostanie ona zainstalowana i uruchomiona, a elementy zostaną dodane do menu **Start** i **Dodaj lub usuń programy** w **Panelu sterowania**.

 Ta strategia sprawdza się najlepiej w przypadku aplikacji wdrażanej dla użytkowników, którzy nie mają stałej łączności sieciowej lub używają połączeń o niskiej przepustowości. Aplikacja jest instalowana z nośnika wymiennego, więc do instalacji nie jest potrzebne połączenie sieciowe, jednak łączność sieciowa jest potrzebna do pobierania aktualizacji aplikacji.

 Aby włączyć tę strategię wdrażania w programie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , kliknij opcję **z dysku CD-ROM lub DVD-ROM** na stronie **jak zainstalowana** w Kreatorze publikacji.

 Aby ręcznie włączyć tę strategię wdrażania, należy zmienić tag **deploymentProvider** w manifeście wdrożenia. (W programie Visual Studio ta właściwość jest uwidaczniana jako **adres URL instalacji** na stronie **Publikuj** projektanta projektu. W *Mage.exe* jest **lokalizacją początkową**.)

## <a name="web-browser-support"></a>Obsługa przeglądarki sieci Web
 Aplikacje, których platformą docelową jest program .NET Framework 3.5, można zainstalować przy użyciu dowolnej przeglądarki.

 Aplikacje, których platformą docelową jest program .NET Framework 2.0, wymagają programu Internet Explorer.

## <a name="see-also"></a>Zobacz też
- [Zabezpieczenia i wdrażanie technologii ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)