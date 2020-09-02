---
title: 'Instrukcje: Instalowanie określonej wersji | Microsoft Docs'
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
ms.openlocfilehash: dde0cefabf0523484ad76ac56f7f2760de8c7acc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64814563"
---
# <a name="how-to-install-a-specific-release-of-visual-studio"></a>Instrukcje: instalowanie określonej wersji programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Często aktualizujemy konfigurację programu Visual Studio, aby uzyskać najbardziej aktualną, zoptymalizowaną wersję naszych opcjonalnych funkcji.  Jeśli jednak chcesz zainstalować wcześniejszą wersję programu Visual Studio 2015 — na przykład wersję wstępnej aktualizacji 1 programu Visual Studio z obsługą systemu iOS, należy wymusić, aby Instalator programu Visual Studio korzystał ze starszej wersji plików manifestu funkcji. W tym artykule opisano, jak to zrobić.

## <a name="installing-the-current-release"></a>Instalowanie bieżącej wersji
 Począwszy od początkowej wersji programu Visual Studio 2015, wielokrotnie Zaktualizowaliśmy aparat instalacji i pliki manifestu.  Oznacza to, że w przypadku pobrania Instalatora sieci Web z witryny internetowej [pobierania programu Visual Studio](https://www.visualstudio.com/downloads/download-visual-studio-vs) na czystej maszynie połączonej z Internetem Instalator instaluje najnowszą aktualizację programu visual Studio 2015, która obejmuje najnowsze ulepszenia produktu, a także nowsze wersje opcjonalnych funkcji i narzędzi.

## <a name="installing-earlier-releases"></a>Instalowanie starszych wersji
 Można utworzyć i zainstalować obraz ISO lub pobrać i uruchomić Instalatora bezpośrednio z programu [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) , a następnie dołączyć plik. exe z dodatkowymi parametrami wiersza polecenia (takimi jak/CustomInstallPath,/Full,/InstallSelectableItems,/norestart itp.), aby kontrolować sposób, w jaki program Visual Studio jest instalowany.

 Poniższa tabela zawiera niektóre określone scenariusze dotyczące określonego momentu i wymagane parametry wiersza polecenia, które należy przekazać do Instalatora wersji Enterprise Edition. (Te same parametry będą współpracować z instalatorami społecznościowymi lub profesjonalnymi).

|Wersja 2015 programu Visual Studio|Co do uruchomienia|Wiersz polecenia do użycia|Jaką konfigurację wykonuje|
|--------------------------------|-----------------|--------------------------|---------------------|
|Visual Studio Enterprise (Najnowsza wersja publiczna)|Visual Studio Enterprise z aktualizacjami (dostępne z   [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015))|`vs_enterprise.exe`**Uwaga:**  Domyślne zachowanie tej instalacji oferuje najnowsze funkcje opcjonalne i w związku z tym nie wymaga żadnych parametrów wiersza polecenia.|Instalator programu Visual Studio użyje najnowszych feed.xml i zainstaluje najnowsze pliki|
|Visual Studio Enterprise Update 3 (Oryginalna aktualizacja 3 bez żadnej dalszej aktualizacji z aktualizacją Update 3 — ERA)|Visual Studio Enterprise RTM (dostępne na [stronie pobierania subskrypcji MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160628.2/enu/feed.xml`|Instalator programu Visual Studio użyje feed.xml, który był dostępny po wydaniu aktualizacji Update 3|
|Visual Studio Enterprise Update 2 (wersja oryginalna Update 2), ale z aktualizacjami wymagającymi wersji Update 3)|Visual Studio Enterprise RTM (dostępne na [stronie pobierania subskrypcji MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/6/B/B/6BBD3561-D764-4F39-AB8E-05356A122545/20160620.2/enu/feed.xml`|Instalator programu Visual Studio użyje feed.xml, który był aktualny przed wydaniem aktualizacji Update 3|
|Visual Studio Enterprise (Oryginalna aktualizacja 2 bez żadnej dalszej aktualizacji Update 2 — aktualizacje ERA)|Visual Studio Enterprise RTM (dostępne na [stronie pobierania subskrypcji MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/0/6/B/06BB0C5C-C767-4250-91DA-AB463377597E/20160405.3/enu/feed.xml`|Instalator programu Visual Studio użyje feed.xml, który był dostępny po wydaniu aktualizacji Update 2|
|Visual Studio Enterprise Update 1 (wersja oryginalna Update 1, ale z aktualizacjami wymagającymi aktualizacji Update 2)|Visual Studio Enterprise RTM (dostępne na [stronie pobierania subskrypcji MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI http://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20160225.3/enu/feed.xml`|Instalator programu Visual Studio użyje feed.xml, który był aktualny przed wydaniem aktualizacji Update 2|
|Visual Studio Enterprise Update 1 (wersja oryginalna Update 1) bez żadnej dalszej aktualizacji Update 1 — aktualizacje ERA.|Visual Studio Enterprise RTM (dostępne na [stronie pobierania subskrypcji MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/2/A/32A1974F-D236-43C1-8981-97DDCBAEF14A/20151201.1/enu/feed.xml`|Instalator programu Visual Studio użyje feed.xml, który był dostępny po wydaniu aktualizacji Update 1|
|Visual Studio Enterprise (oryginalna RTM, ale z aktualizacjami wymagającymi aktualizacji wstępnej 1)|Visual Studio Enterprise RTM (dostępne na  [stronie pobierania subskrypcji MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/3/6/1/36188D5F-479F-4A46-BF55-6AE5928D1EBB/20151102.3/enu/feed.xml`|Instalator programu Visual Studio użyje feed.xml, który był aktualny przed wydaniem aktualizacji Update 1|
|Visual Studio Enterprise (oryginalna RTM bez aktualizacji)|Visual Studio Enterprise RTM (dostępne na [stronie pobierania subskrypcji MSDN](https://msdn.microsoft.com/subscriptions/downloads/))|`vs_enterprise.exe /OverrideFeedURI https://download.microsoft.com/download/5/7/B/57BF5016-E4F0-4EB5-BE27-2BFA87E7723F/20150713.1/enu/feed.xml`|Instalator programu Visual Studio użyje feed.xml, która była dostępna po wydaniu wersji RTM|

> [!IMPORTANT]
> W zależności od języka, którego chcesz użyć, Zastąp ciąg "PLK" (w przypadku języka angielskiego) jedną z następujących wartości:
>
> - CHS (dla języka chińskiego (uproszczonego))
>   - CHT (dla języka chińskiego (tradycyjnego))
>   - CSY (dla Czech)
>   - DEU (dla języka niemieckiego)
>   - ESN (dla języka hiszpańskiego)
>   - FRA (dla języka francuskiego)
>   - Ita (dla języka włoskiego)
>   - JPA (dla języka japońskiego)
>   - Kor (dla koreański)
>   - PLK (dla Polski)
>   - PTB (dla języka portugalskiego)
>   - jednostek ru (dla rosyjski)
>   - ZMN (dla turecki)

## <a name="see-also"></a>Zobacz też
 [Przewodnik administratora programu Visual Studio](../install/visual-studio-administrator-guide.md)