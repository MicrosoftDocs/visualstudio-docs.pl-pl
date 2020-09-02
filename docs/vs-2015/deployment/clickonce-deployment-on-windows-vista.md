---
title: Wdrożenie ClickOnce w systemie Windows Vista | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675475"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Wdrożenie ClickOnce w systemie Windows Vista
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tworzenie aplikacji w programie Visual Studio na potrzeby kontroli konta użytkownika w systemie Windows Vista zwykle generuje osadzony manifest zakodowany jako dane binarne XML w pliku wykonywalnym aplikacji. Ponieważ aplikacje COM w technologii ClickOnce i bez rejestracji wymagają manifestu zewnętrznego, program Visual Studio generuje plik dla tego typu projektów zawierających dane kontroli konta użytkownika zamiast osadzonego manifestu. Domyślnie program Visual Studio używa informacji z pliku o nazwie App. manifest, aby generować zewnętrzne informacje manifestu kontroli konta użytkownika (na potrzeby technologii ClickOnce i wdrożenia COM bez rejestracji) lub osadzić je w pliku wykonywalnym aplikacji (we wszystkich innych przypadkach). Program Visual Studio udostępnia następujące opcje generowania manifestu:  
  
- Użyj osadzonego manifestu. Osadź dane funkcji Kontrola konta użytkownika w pliku wykonywalnym aplikacji i Uruchom jako zwykły użytkownik.  
  
   Jest to ustawienie domyślne (chyba że używasz technologii ClickOnce). To ustawienie będzie obsługiwać zwykły sposób działania programu Visual Studio w systemie Windows Vista; oznacza to, że generacja wewnętrznego i zewnętrznego manifestu, zarówno przy użyciu `AsInvoker` .  
  
- Użyj manifestu zewnętrznego. Wygeneruj manifest zewnętrzny przy użyciu pliku App. manifest.  
  
   Spowoduje to wygenerowanie tylko manifestu zewnętrznego przy użyciu informacji w pliku App. manifest. Po opublikowaniu aplikacji przy użyciu technologii ClickOnce lub COM bez rejestracji program Visual Studio dodaje do projektu App. manifest i dodaje tę opcję.  
  
- Nie używaj manifestu. Utwórz aplikację bez manifestu.  
  
   Takie podejście jest również znane jako *Wirtualizacja*. Użyj tej opcji, aby zapewnić zgodność z istniejącymi aplikacjami z wcześniejszych wersji programu Visual Studio.  
  
  Nowe właściwości są dostępne na stronie **aplikacji** projektanta projektu (tylko w przypadku projektów Visual C#) i w formacie pliku projektu programu MSBuild.  
  
  Należy pamiętać, że metoda konfigurowania generowania manifestu kontroli konta użytkownika w środowisku IDE programu Visual Studio różni się w zależności od typu projektu (Visual C# i Visual Basic).  
  
  Aby uzyskać informacje o konfigurowaniu projektów Visual C# na potrzeby generowania manifestu, zobacz [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md).  
  
  Aby uzyskać informacje o konfigurowaniu Visual Basic projektów na potrzeby generowania manifestu, zobacz [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo i wdrażanie technologii ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Uprawnienia użytkownika i program Visual Studio](https://msdn.microsoft.com/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
