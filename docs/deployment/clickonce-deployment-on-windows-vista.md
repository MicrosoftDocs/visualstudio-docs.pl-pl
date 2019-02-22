---
title: Wdrożenie ClickOnce w systemie Windows Vista | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56600106"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Wdrożenie ClickOnce w systemie Windows Vista

Tworzenie aplikacji w programie Visual Studio dla kontroli konta użytkownika (UAC) w Windows Vista zwykle generuje manifestu osadzonego zakodowane jako dane binarne dane XML w pliku wykonywalnym aplikacji.  ClickOnce i rejestracji wolnego modelu COM aplikacji wymagają manifestem zewnętrznym, dzięki czemu program Visual Studio generuje plik dla tych projektów zawierających dane funkcji Kontrola konta użytkownika zamiast wbudowanym manifeście. W przypadku wdrożeń technologii ClickOnce i rejestracji wolnego modelu COM, program Visual Studio używa informacji z pliku o nazwie *app.manifest* wygenerować informacje manifestu UAC zewnętrznych. Dla wszystkich innych przypadkach program Visual Studio osadza dane funkcji Kontrola konta użytkownika w pliku wykonywalnym aplikacji.

Visual Studio zawiera następujące opcje do generowania manifestu:

- Użyj manifestu osadzonego. Osadzone dane funkcji Kontrola konta użytkownika w pliku wykonywalnym aplikacji, a następnie uruchom jako zwykły użytkownik.

   To ustawienie domyślne (chyba że używasz ClickOnce). To ustawienie sprzyja zwykły sposób, w którym działa program Visual Studio w systemie Windows Vista, za pomocą Generowanie wewnętrznego i zewnętrznego manifestu za pomocą `AsInvoker`.

- Użyj manifestem zewnętrznym. Generowanie manifestem zewnętrznym przy użyciu *app.manifest*.

   Korzystając z informacji podanych w spowoduje to wygenerowanie manifestem zewnętrznym *app.manifest*. Podczas publikowania aplikacji za pomocą technologii ClickOnce lub rejestracji wolnego modelu COM, program Visual Studio dodaje *app.manifest* do projektu, a następnie dodaje tę opcję.

- Użyj nie manifestu. Utwórz aplikację bez manifestu.

   To podejście jest nazywane również *wirtualizacji*. Użyj tej opcji w celu zgodności z istniejącymi aplikacjami z wcześniejszych wersji programu Visual Studio.

  Nowe właściwości są dostępne na **aplikacji** strony Projektant projektu (Visual C# tylko dla projektów) i formatu pliku projektu MSBuild.

  Metoda na temat konfigurowania Generowanie manifestu UAC w środowisku IDE programu Visual Studio różni się w zależności od typu projektu (Visual C# lub Visual Basic).

  * Aby uzyskać informacje o konfigurowaniu projektów języka Visual C# do generowania manifestu, zobacz [strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md).

  * Aby uzyskać informacje o konfigurowaniu projektów języka Visual Basic do generowania manifestu, zobacz [strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).

## <a name="see-also"></a>Zobacz także
- [Wdrażania i zabezpieczeń ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Uprawnienia użytkownika i program Visual Studio](https://msdn.microsoft.com/library/d5c55084-1e7b-4b61-b478-137db01c0fc0)
- [Strona aplikacji, Projektant projektu (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Strona aplikacji, Projektant projektu (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)