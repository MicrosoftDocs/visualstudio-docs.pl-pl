---
title: Wdrożenie ClickOnce w systemie Windows Vista | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- UAC manifest generation
- ClickOnce deployment, Windows
- manifest generation
- Windows, ClickOnce deployment
ms.assetid: b21a0ebc-0ff6-4f49-8993-7d1ad3f8cac2
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e25f9da960b1de8acb1950b2bdd3ab7e61409f17
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675475"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Wdrożenie ClickOnce w systemie Windows Vista
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tworzenie aplikacji w programie Visual Studio dla kontroli konta użytkownika (UAC) w Windows Vista zwykle generuje manifestu osadzonego zakodowane jako dane binarne dane XML w pliku wykonywalnym aplikacji. Ponieważ ClickOnce i rejestracji wolnego modelu COM aplikacji wymaga manifestem zewnętrznym, program Visual Studio generuje plik dla tych typów projektów zawierających dane funkcji Kontrola konta użytkownika, zamiast wbudowanym manifeście. Domyślnie program Visual Studio używa informacji z pliku o nazwie app.manifest do generowania zewnętrznych informacji manifestu kontroli konta użytkownika (w przypadku wdrażania ClickOnce i rejestracji wolnego modelu COM) lub można ją osadzić w pliku wykonywalnym aplikacji (w przypadku wszystkich innych przypadkach). Visual Studio zawiera następujące opcje do generowania manifestu:  
  
- Użyj manifestu osadzonego. Osadzone dane funkcji Kontrola konta użytkownika w pliku wykonywalnym aplikacji i Uruchom jako zwykły użytkownik.  
  
   To ustawienie domyślne (chyba że używasz ClickOnce). To ustawienie będzie obsługiwać zwykły sposób, w którym działa program Visual Studio w systemie Windows Vista; oznacza to, generowania manifestu wewnętrznych i zewnętrznych, zarówno za pomocą `AsInvoker`.  
  
- Użyj manifestem zewnętrznym. Generowanie manifestem zewnętrznym przy użyciu app.manifest.  
  
   Spowoduje to wygenerowanie manifestem zewnętrznym, korzystając z informacji podanych w app.manifest. Gdy spróbujesz opublikować aplikację przy użyciu technologii ClickOnce lub COM bez rejestrowania programu Visual Studio dodaje app.manifest do projektu i dodaje tę opcję.  
  
- Użyj nie manifestu. Utwórz aplikację bez manifestu.  
  
   To podejście jest nazywane również *wirtualizacji*. Użyj tej opcji w celu zgodności z istniejącymi aplikacjami z wcześniejszych wersji programu Visual Studio.  
  
  Nowe właściwości są dostępne na **aplikacji** strony Projektant projektu (Visual C# tylko dla projektów) i formatu pliku projektu MSBuild.  
  
  Należy zauważyć, że metoda na temat konfigurowania Generowanie manifestu UAC w środowisku IDE programu Visual Studio różni się w zależności od typu projektu (Visual C# i Visual Basic).  
  
  Aby uzyskać informacje o konfigurowaniu projektów języka Visual C# do generowania manifestu, zobacz [strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md).  
  
  Aby uzyskać informacje o konfigurowaniu projektów języka Visual Basic do generowania manifestu, zobacz [strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażania i zabezpieczeń ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Uprawnienia użytkownika i program Visual Studio](https://msdn.microsoft.com/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
