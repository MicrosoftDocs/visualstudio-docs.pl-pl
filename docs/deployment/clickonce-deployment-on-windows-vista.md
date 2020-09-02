---
title: Wdrożenie ClickOnce w systemie Windows Vista | Microsoft Docs
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4beefddd429384fadda71d9742e8c0fac606c38e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62900505"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Wdrażanie technologii ClickOnce w systemie Windows Vista

Tworzenie aplikacji w programie Visual Studio na potrzeby kontroli konta użytkownika w systemie Windows Vista zwykle generuje osadzony manifest zakodowany jako dane binarne XML w pliku wykonywalnym aplikacji.  Aplikacje COM i bezpłatnej rejestracji wymagają manifestu zewnętrznego, dlatego program Visual Studio generuje plik dla tych projektów zawierających dane UAC zamiast osadzonego manifestu. W przypadku wdrożeń ClickOnce i niebezpłatnych rejestracji COM program Visual Studio używa informacji z pliku o nazwie *App. manifest* do generowania informacji o zewnętrznym manifeście funkcji kontroli konta użytkownika. We wszystkich innych przypadkach program Visual Studio osadza dane funkcji Kontrola konta użytkownika w pliku wykonywalnym aplikacji.

Program Visual Studio udostępnia następujące opcje generowania manifestu:

- Użyj osadzonego manifestu. Osadź dane funkcji Kontrola konta użytkownika w pliku wykonywalnym aplikacji i Uruchom jako zwykły użytkownik.

   Jest to ustawienie domyślne (chyba że używasz technologii ClickOnce). To ustawienie obsługuje zazwyczaj sposób, w jaki program Visual Studio działa w systemie Windows Vista, z generowaniem wewnętrznego i zewnętrznego manifestu przy użyciu `AsInvoker` .

- Użyj manifestu zewnętrznego. Wygeneruj manifest zewnętrzny przy użyciu pliku *App. manifest*.

   Spowoduje to wygenerowanie tylko manifestu zewnętrznego przy użyciu informacji w pliku *App. manifest*. Po opublikowaniu aplikacji przy użyciu technologii ClickOnce lub COM bez rejestracji program Visual Studio dodaje do projektu *App. manifest* , a następnie dodaje tę opcję.

- Nie używaj manifestu. Utwórz aplikację bez manifestu.

   Takie podejście jest również znane jako *Wirtualizacja*. Użyj tej opcji, aby zapewnić zgodność z istniejącymi aplikacjami z wcześniejszych wersji programu Visual Studio.

  Nowe właściwości są dostępne na stronie **aplikacji** projektanta projektu (tylko w przypadku projektów Visual C#) i w formacie pliku projektu programu MSBuild.

  Metoda konfigurowania generowania manifestu kontroli konta użytkownika w środowisku IDE programu Visual Studio różni się w zależności od typu projektu (Visual C# lub Visual Basic).

  * Aby uzyskać informacje o konfigurowaniu projektów Visual C# na potrzeby generowania manifestu, zobacz [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md).

  * Aby uzyskać informacje o konfigurowaniu Visual Basic projektów na potrzeby generowania manifestu, zobacz [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).

## <a name="see-also"></a>Zobacz też
- [Zabezpieczenia i wdrażanie technologii ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Uprawnienia użytkownika i program Visual Studio](https://msdn.microsoft.com/library/d5c55084-1e7b-4b61-b478-137db01c0fc0)
- [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)