---
title: Visual Studio i Xamarin | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: 1da4064f-af69-472c-8f31-98484be5f790
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: 098d94a1aed9020271db5010e278a4aa8fc68330
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442127"
---
# <a name="visual-studio-and-xamarin"></a>Visual Studio i Xamarin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Xamarin to platforma do tworzenia aplikacji mobilnych, do tworzenia natywnych dla systemów iOS, Android i Windows aplikacje z poziomu wspólnego C#/.NET kodzie podstawowym, osiągnięcie 75% do prawie 100% ponownego użycia kodu między platformami. Aplikacje napisane z rozwiązaniami Xamarin i C# mają pełny dostęp do podstawowych interfejsów API platformy i możliwość tworzenia natywne interfejsy użytkownika i Kompiluj do pakietów specyficznych dla platformy, więc ma little wpływ na wydajność środowiska uruchomieniowego. (Uwaga: Program Xamarin obsługuje również F#, ale w tej dokumentacji koncentruje się na C# tylko. Visual Basic nie jest obsługiwana w tej chwili.)  
  
 Jednak lepiej deweloperom zapoznać się z C# .NET i Visual Studio będzie korzysta z takich samych możliwości i wydajność podczas pracy z platformą Xamarin dla aplikacji mobilnych, w tym zdalnego debugowania na urządzeniach z systemem Android, iOS i Windows — bez konieczności uczenia się kodu natywnego w językach Objective-C lub Java. Jest mały Zaskoczenie, a następnie oznacza wiele aplikacji o wysokiej wydajności przy użyciu projektowania atrakcyjnych interfejsów użytkownika — takie jak NASCAR, kierownik działu Aviva i MixRadio — utworzone za pomocą platformy Xamarin.  
  
 Ta dokumentacja pomoże Ci ocenić pełnego zestawu funkcji **programu Visual Studio za pomocą platformy Xamarin** do tworzenia tych środowisk.  
  
- Rozpoczynać [Instalator i instalacja](../cross-platform/setup-and-install.md), proces, który zajmie trochę czasu (zwykle 2 – 4 godzin w zależności od szybkości połączenia internetowego, co została już zainstalowana i wybrane opcje).  
  
- Gdy pliki instalacyjne są uruchomione, można [Dowiedz się więcej o programowaniu rozwiązań mobilnych za pomocą platformy Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) który poinformuje o rodzaju Xamarin, porównaj zestawu narzędzi Xamarin.Forms do natywnego interfejsu użytkownika i nie tylko.  
  
- Po zakończeniu instalacji [Sprawdź swoje środowisko Xamarin](../cross-platform/verify-your-xamarin-environment.md).  
  
- Zakończ za pośrednictwem tego samouczka [opanowaniu podstaw tworzenia aplikacji przy użyciu zestawu narzędzi Xamarin.Forms w programie Visual Studio](../cross-platform/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md).  
  
  Możesz pracować z wszystkie funkcje platformy Xamarin przy użyciu [dowolnej wersji programu Visual Studio 2015](https://www.visualstudio.com/vs-2015-product-editions) (Community, Professional i Enterprise). Należy zauważyć, że począwszy od 31 marca 2016 r. platformy Xamarin jest zawarty we wszystkich edycjach Visual Studio 2015 i nie wymaga już oddzielnej licencji. Dla programu Visual Studio 2013, możesz zainstalować program Xamarin oddzielnie, jako [Instalator i instalacja](../cross-platform/setup-and-install.md) temacie.  
  
> [!NOTE]
> W instrukcjach opisano konfigurację komputera Najłatwiejszym i najbardziej prostego te, które mają tło Windows i programu Visual Studio. W przypadku tej konfiguracji cały proces tworzenia jest uproszczone, ponieważ należy do interakcji z komputerem Mac, aby użyć symulatora systemu iOS i urządzenie powiązane. Zamiast tego pochodzących z komputerów Mac w tle, firma Microsoft zaleca uruchamianie programu Visual Studio wewnątrz równoleżników/VMWare lub za pomocą platformy Xamarin Studio Community. Zapoznaj się [Instalator, instalacja i weryfikacja dla użytkowników komputerów Mac](../cross-platform/setup-install-and-verifications-for-mac-users.md) instrukcje.  
  
> [!NOTE]
> Jeśli szukasz rozwiązanie programowanie dla wielu platform oparte na kodzie HTML i CSS, zapoznaj się z programu Visual Studio Tools for Apache Cordova zgodnie z opisem w [programowanie dla wielu Platform w programie Visual Studio](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#HTML).
