---
title: Wdrożenie ClickOnce w systemie Windows Vista | Microsoft Docs
description: Dowiedz się, jak program Visual Studio generuje zewnętrzny manifest funkcji kontroli konta użytkownika dla aplikacji ClickOnce i Registration-Free COM, które wymagają manifestu zewnętrznego.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c2e09225339a87c55c31d27d26b129e199385e99
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383082"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Wdrażanie technologii ClickOnce w systemie Windows Vista

Tworzenie aplikacji w programie Visual Studio na potrzeby kontroli konta użytkownika w systemie Windows Vista zwykle generuje osadzony manifest zakodowany jako dane binarne XML w pliku wykonywalnym aplikacji.  Aplikacje ClickOnce i Registration-Free COM wymagają manifestu zewnętrznego, dlatego program Visual Studio generuje plik dla tych projektów zawierających dane kontroli konta użytkownika zamiast osadzonego manifestu. W przypadku wdrożeń ClickOnce i Registration-Free COM program Visual Studio używa informacji z pliku o nazwie *App. manifest* do generowania informacji o zewnętrznym manifeście funkcji kontroli konta użytkownika. We wszystkich innych przypadkach program Visual Studio osadza dane funkcji Kontrola konta użytkownika w pliku wykonywalnym aplikacji.

Program Visual Studio udostępnia następujące opcje generowania manifestu:

- Użyj osadzonego manifestu. Osadź dane funkcji Kontrola konta użytkownika w pliku wykonywalnym aplikacji i Uruchom jako zwykły użytkownik.

   Jest to ustawienie domyślne (chyba że używasz technologii ClickOnce). To ustawienie obsługuje zazwyczaj sposób, w jaki program Visual Studio działa w systemie Windows Vista, z generowaniem wewnętrznego i zewnętrznego manifestu przy użyciu `AsInvoker` .

- Użyj manifestu zewnętrznego. Wygeneruj manifest zewnętrzny przy użyciu pliku *App. manifest*.

   Spowoduje to wygenerowanie tylko manifestu zewnętrznego przy użyciu informacji w pliku *App. manifest*. Po opublikowaniu aplikacji przy użyciu technologii ClickOnce lub Registration-Free COM program Visual Studio dodaje do projektu *App. manifest* , a następnie dodaje tę opcję.

- Nie używaj manifestu. Utwórz aplikację bez manifestu.

   Takie podejście jest również znane jako *Wirtualizacja*. Użyj tej opcji, aby zapewnić zgodność z istniejącymi aplikacjami z wcześniejszych wersji programu Visual Studio.

  Nowe właściwości są dostępne na stronie **aplikacji** projektanta projektu (tylko w przypadku projektów Visual C#) i w formacie pliku projektu programu MSBuild.

  Metoda konfigurowania generowania manifestu kontroli konta użytkownika w środowisku IDE programu Visual Studio różni się w zależności od typu projektu (Visual C# lub Visual Basic).

  * Aby uzyskać informacje o konfigurowaniu projektów Visual C# na potrzeby generowania manifestu, zobacz [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md).

  * Aby uzyskać informacje o konfigurowaniu Visual Basic projektów na potrzeby generowania manifestu, zobacz [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).

## <a name="see-also"></a>Zobacz też
- [Zabezpieczenia i wdrażanie technologii ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Uprawnienia użytkownika i program Visual Studio](/previous-versions/ms165100(v=vs.100))
- [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)