---
title: 'Instrukcje: Instalowanie określonej wersji | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- install a specific release, Visual Studio
ms.assetid: d69ad0f8-f0a0-438e-a0ef-777c4868f139
caps.latest.revision: 20
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: b5f74512d0c035a82845d77f4b3df12633036f03
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54756363"
---
# <a name="how-to-install-a-specific-release-of-visual-studio"></a>Instrukcje: Instalowanie określonej wersji programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Firma Microsoft aktualizuje Instalatora programu Visual Studio często tak, aby uzyskać najbardziej aktualnych i zautomatyzowanych wersję nasze funkcje opcjonalne.  Ale jeśli chcesz zainstalować starszej wersji programu Visual Studio 2015 — na przykład przed aktualizacją 1 wydania programu Visual Studio z obsługą systemu iOS — a następnie należy wymusić instalację programu Visual Studio do korzystają z wcześniejszej wersji swoich plików manifestu funkcji. W tym artykule opisano, jak to zrobić.

## <a name="installing-the-current-release"></a>Instalowania bieżącej wersji
 Od początkowej wersji programu Visual Studio 2015 Zaktualizowaliśmy aparat Instalatora i plików manifestu kilka razy.  Oznacza to, że jeśli możesz pobrać Instalator internetowy [pobieranie Visual Studio](https://www.visualstudio.com/downloads/download-visual-studio-vs) witryny sieci Web na maszynie zawsze przejrzyste i podłączonej do Internetu, instalowana przez Instalator najnowszy program Visual Studio 2015: Aktualizacja, która obejmuje najnowsze ulepszenia produktu oraz nowszymi, najnowsze wersje narzędzia i funkcje opcjonalne.

## <a name="installing-earlier-releases"></a>Instalowanie starszej wersji
 Możesz tworzyć i instalowania obrazu ISO lub można pobrać i uruchomić Instalatora bezpośrednio z [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) i Dołącz plik .exe, za pomocą dodatkowych parametrów wiersza polecenia (takich jak /CustomInstallPath, / zapełniony, / InstallSelectableItems, / norestart / itp.) Aby kontrolować sposób przeprowadzania instalacji programu Visual Studio.

 Poniższa tabela zawiera niektóre konkretnych scenariuszy w momencie i niezbędne parametry wiersza polecenia, które należy przekazać do Instalator Enterprise edition. (Te same parametry będzie działać z Community i Professional edition instalatory także).

|Wersja programu Visual Studio 2015|Co do uruchamiania|Wiersza polecenia do użycia|Jaka konfiguracja jest|
|--------------------------------|-----------------|--------------------------|---------------------|
|Program Visual Studio Enterprise (najnowszą wersją publiczną)|Visual Studio Enterprise z aktualizacji (dostępnym [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015))|`vs_enterprise.exe` **Uwaga:**  Domyślne zachowanie tej instalacji oferuje najnowsze funkcje opcjonalne i dlatego nie jest wymagane parametry wiersza polecenia.|Instalator programu Visual Studio będzie używać najnowszych feed.xml i zainstalować najnowsze pliki|
|Visual Studio Enterprise Update 3 (oryginalny aktualizacja Update 3 bez żadnych dalszych aktualizacji 3 ery aktualizacji)|Program Visual Studio Enterprise RTM (dostępne z [stronę pobierania subskrypcje MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160628.2/enu/feed.xml`|Instalator programu Visual Studio będzie używać feed.xml, która była dostępna, po wydaniu aktualizacji 3|
|Visual Studio Enterprise Update 2 (oryginał Update 2, ale z aktualizacjami tego wstępnie aktualizacji Update 3)|Program Visual Studio Enterprise RTM (dostępne z [stronę pobierania subskrypcje MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160620.2/enu/feed.xml`|Instalator programu Visual Studio będzie używać feed.xml, aktualna przed Update 3 wydania|
|Program Visual Studio Enterprise (oryginalny Update 2 bez żadnych dalszych aktualizacji 2 ery aktualizacji)|Program Visual Studio Enterprise RTM (dostępne z [stronę pobierania subskrypcje MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/0/6/B/06BB0C5C-C767-4250-91DA-AB463377597E/20160405.3/enu/feed.xml`|Instalator programu Visual Studio będzie używać feed.xml, która była dostępna, po wydaniu aktualizacji 2|
|Visual Studio Enterprise Update 1 (oryginał Update 1, ale z aktualizacjami tego wstępnie aktualną Update 2)|Program Visual Studio Enterprise RTM (dostępne z [stronę pobierania subskrypcje MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20160225.3/enu/feed.xml`|Instalator programu Visual Studio będzie używać feed.xml, aktualna przed Update 2 wydania|
|Visual Studio Enterprise Update 1 (oryginalny aktualizacji 1 bez wszelkie dalsze aktualizacje ery 1 Update)|Program Visual Studio Enterprise RTM (dostępne z [stronę pobierania subskrypcje MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20151201.1/enu/feed.xml`|Instalator programu Visual Studio będzie używać feed.xml, która była dostępna, po wydaniu aktualizacji 1|
|Program Visual Studio Enterprise (Oryginalna RTM, ale z aktualizacji tej wstępnie aktualną Update 1)|Program Visual Studio Enterprise RTM (dostępne z [stronę pobierania subskrypcje MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/6/1/36188D5F-479F-4A46-BF55-6AE5928D1EBB/20151102.3/enu/feed.xml`|Instalator programu Visual Studio będzie używać feed.xml, aktualna przed Update 1 wydania|
|Program Visual Studio Enterprise (oryginalny RTM z żadnych aktualizacji)|Program Visual Studio Enterprise RTM (dostępne z [stronę pobierania subskrypcje MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/5/7/B/57BF5016-E4F0-4EB5-BE27-2BFA87E7723F/20150713.1/enu/feed.xml`|Instalator programu Visual Studio będzie używać feed.xml, która była dostępna, po wydaniu wersji RTM|

> [!IMPORTANT]
>  W zależności od języka, którego chcesz używać Zastąp "tekst enu" (w języku angielskim) przy użyciu jednego z następujących wartości:
>
> - (CHS) (dla języka chińskiego (uproszczonego))
>   -   (CHT) (w przypadku chiński tradycyjny)
>   -   CSY (w przypadku czeski)
>   -   DEU (dla języka niemieckiego)
>   -   Hiszpański (dla języka hiszpańskiego)
>   -   (FRA) (w przypadku francuski)
>   -   (ITA) (w przypadku włoska)
>   -   rozwiązaniami jpa (w języku japońskim)
>   -   koreański (w przypadku koreański)
>   -   PLK (w przypadku Polski)
>   -   PTB (w przypadku portugalski)
>   -   jednostki zarezerwowane (w przypadku rosyjski)
>   -   TRK (w przypadku turecki)

## <a name="see-also"></a>Zobacz też
 [Podręcznik administratora programu Visual Studio](../install/visual-studio-administrator-guide.md)