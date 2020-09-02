---
title: Visual Studio i Xamarin | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: 1da4064f-af69-472c-8f31-98484be5f790
caps.latest.revision: 14
ms.author: crdun
manager: crdun
ms.openlocfilehash: 098d94a1aed9020271db5010e278a4aa8fc68330
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64828386"
---
# <a name="visual-studio-and-xamarin"></a>Visual Studio i Xamarin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Xamarin to platforma programistyczna aplikacji mobilnych do tworzenia natywnych aplikacji dla systemów iOS, Android i Windows przy użyciu wspólnej bazy kodu/.NET w języku C#, która zapewnia 75% do niemal 100% kodu na różnych platformach. Aplikacje zaprojektowane z platformą Xamarin i C# mają pełny dostęp do podstawowych interfejsów API platformy oraz możliwość tworzenia natywnych interfejsów użytkownika i kompilowania ich w pakiety specyficzne dla platformy, co znacznie wpływa na wydajność środowiska uruchomieniowego. (Uwaga: platforma Xamarin obsługuje również język F #, ale ta dokumentacja będzie koncentrować się tylko na języku C#. Visual Basic nie jest w tej chwili obsługiwana.)  
  
 Mimo że deweloperzy znający Języki C#, .NET i Visual Studio będą korzystać z tej samej mocy i wydajności podczas pracy z programem Xamarin dla aplikacji mobilnych, w tym z debugowaniem zdalnym na urządzeniach z systemem Android, iOS i Windows — bez konieczności uczenia natywnych języków kodowania, takich jak "obiektyw-C" lub Java. Jest to nieco niespodziewane, więc wiele aplikacji o wysokiej wydajności z atrakcyjnymi interfejsami użytkownika, takimi jak NASCAR, Aviva i MixRadio, zostały skompilowane przy użyciu platformy Xamarin.  
  
 Ta dokumentacja pomaga w ocenie pełnych możliwości programu **Visual Studio z** platformą Xamarin w celu utworzenia tych środowisk.  
  
- Rozpocznij od [instalacji i instalacji](../cross-platform/setup-and-install.md), proces, który zajmie trochę czasu (zwykle 2-4 godzin w zależności od szybkości połączenia internetowego, zainstalowanego już programu oraz wybranych opcji).  
  
- Podczas gdy Instalatory są uruchomione, możesz [dowiedzieć się więcej na temat tworzenia aplikacji mobilnych za pomocą platformy Xamarin](../cross-platform/learn-about-mobile-development-with-xamarin.md) , które poinformują o rodzaju środowiska Xamarin, porównać z platformą Xamarin. Forms z natywnym interfejsem użytkownika i nie tylko.  
  
- Po zakończeniu instalacji [Sprawdź środowisko platformy Xamarin](../cross-platform/verify-your-xamarin-environment.md).  
  
- Przejdź do samouczka [Poznaj podstawy tworzenia aplikacji za pomocą platformy Xamarin. Forms w programie Visual Studio](../cross-platform/learn-app-building-basics-with-xamarin-forms-in-visual-studio.md).  
  
  Możesz korzystać ze wszystkich funkcji platformy Xamarin za pomocą [dowolnej wersji programu Visual Studio 2015](https://www.visualstudio.com/vs-2015-product-editions) (Community, Professional i Enterprise). Zwróć uwagę na to, że od marca 31 2016 środowisko Xamarin jest dołączone do wszystkich wersji programu Visual Studio 2015 i nie wymaga już oddzielnej licencji. Visual Studio 2013 można zainstalować w środowisku Xamarin osobno, zgodnie z opisem w temacie [Instalacja i instalacja](../cross-platform/setup-and-install.md) .  
  
> [!NOTE]
> Te instrukcje opisują najprostszą i najbardziej prostą konfigurację komputera dla tych, które mają tło systemu Windows i programu Visual Studio. W tej konfiguracji ogólne środowisko programistyczne jest uproszczone, ponieważ należy tylko korzystać z komputera Mac do korzystania z symulatora systemu iOS i urządzenia tetheringu. Jeśli zamiast tego będziesz korzystać z tła Mac, zalecamy uruchomienie programu Visual Studio wewnątrz równoległych/VMWare lub przy użyciu Xamarin Studio społeczność. Instrukcje można znaleźć w tematach [Instalacja, instalacja i weryfikacja dla użytkowników komputerów Mac](../cross-platform/setup-install-and-verifications-for-mac-users.md) .  
  
> [!NOTE]
> Jeśli szukasz rozwiązania deweloperskiego dla wielu platform na podstawie kodu HTML i CSS, zapoznaj się z Visual Studio Tools Apache Cordova, zgodnie z opisem w temacie [programowanie Międzyplatformowe w programie Visual Studio](../cross-platform/cross-platform-mobile-development-in-visual-studio.md#HTML).
