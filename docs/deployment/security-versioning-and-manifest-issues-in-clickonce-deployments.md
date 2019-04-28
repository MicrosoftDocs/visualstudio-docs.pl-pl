---
title: Zabezpieczenia, przechowywanie wersji i problemy z manifestami we wdrożeniach ClickOnce | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- versioning, ClickOnce applications
- ClickOnce applications, Windows Vista User Account Control
- ClickOnce applications, versioning issues
- security, ClickOnce applications
- Windows 7, ClickOnce deployments
- ClickOnce applications, manifest issues
- User Account Control, ClickOnce applications
- Windows Vista, ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, security issues
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c87fc29b24b3c5ab4bd59d9cca25113f82895ff4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62928217"
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>Zabezpieczenia, przechowywanie wersji i problemy z manifestami we wdrożeniach ClickOnce

Istnieją różne problemy z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zabezpieczenia, przechowywanie wersji aplikacji i manifestu składni i semantykę, która może spowodować, że [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia nie powiodła się.

## <a name="clickonce-and-windows-vista-user-account-control"></a>ClickOnce i kontrola konta użytkownika programu Windows Vista

W [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)], aplikacje, które domyślnie są uruchamiane jako użytkownik standardowy, nawet wtedy, gdy bieżący użytkownik jest zalogowany za pomocą konta mającego uprawnienia administratora. Jeśli aplikacja musi wykonać akcję, która musi mieć uprawnienia administratora, informuje system operacyjny, który następnie monituje użytkownika o wprowadzenie poświadczeń administratora. Tej funkcji, która nosi nazwę kontroli konta użytkownika (UAC), uniemożliwia aplikacji wprowadzania zmian, które mogą mieć wpływ na cały system operacyjny bez wyraźnej zgody użytkownika. Aplikacje Windows deklarują, potrzebują tego podnoszenia poziomu uprawnień, określając `requestedExecutionLevel` atrybutu w `trustInfo` części w manifeście aplikacji.

Ze względu na ryzyko ujawnienia aplikacji na ataki podniesienie poziomu zabezpieczeń [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje nie mogą zażądać podnoszenia poziomu uprawnień, włączenie funkcji Kontrola konta użytkownika dla klienta. Wszelkie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikację, która próbuje ustawić jej `requestedExecutionLevel` atrybutu `requireAdministrator` lub `highestAvailable` nie zostaną zainstalowane na [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].

W niektórych przypadkach Twoje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja może spróbować uruchomić z uprawnieniami administratora z powodu logiki wykrywania Instalatora na [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]. W takim przypadku można ustawić `requestedExecutionLevel` atrybutu w manifeście aplikacji do `asInvoker`. Spowoduje to aplikacja do uruchomienia bez podniesienia uprawnień. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] automatycznie dodaje ten atrybut do wszystkich manifestów aplikacji.

Jeśli tworzysz aplikację, która wymaga uprawnień administratora dla całego cyklu życia aplikacji, należy rozważyć, wdrażanie aplikacji przy użyciu technologii Instalatora Windows (MSI), zamiast tego. Aby uzyskać więcej informacji, zobacz [podstawowe informacje dotyczące Instalatora Windows](../extensibility/internals/windows-installer-basics.md).

## <a name="online-application-quotas-and-partial-trust-applications"></a>Limity przydziału aplikacji w trybie online i aplikacji częściowej relacji zaufania

Jeśli Twoje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] działa aplikacja online zamiast za pomocą instalacji, musi mieścić się w limitu przydziału dla aplikacji w trybie online. Ponadto aplikacji sieci, która jest uruchamiana w częściowej relacji zaufania, takich jak z ograniczonym zestawem uprawnień zabezpieczeń nie może przekraczać połowę rozmiar przydziału.

Aby uzyskać więcej informacji i instrukcje dotyczące sposobu zmiany limitu przydziału aplikacja online, zobacz [Przegląd pamięci podręcznej ClickOnce](../deployment/clickonce-cache-overview.md).

## <a name="versioning-issues"></a>Problemy z wersjonowaniem

Mogą wystąpić problemy, jeśli Przypisz silne nazwy do zestawu i zwiększ numer wersji zestawu, aby uwzględnić aktualizację aplikacji. Każdy zespół skompilowane z odwołaniem do zestawu z silną nazwą samego powodującej lub podejmie próbę odwoływać się do starszej wersji zestawu. Zestaw spróbuje to, ponieważ zestaw jest stara wartość wersji w swoim żądaniu powiązania.

Załóżmy na przykład mieć zestawu z silną nazwą we własnym projekcie za pomocą wersji 1.0.0.0. Po kompilacji zestawu, Dodaj odwołanie do projektu, który zawiera głównej aplikacji. Jeśli aktualizacja zestawu, Zwiększ wersji 1.0.0.1 i spróbuj wdrożyć ją bez również konieczności ponownego kompilowania aplikacji Aplikacja nie będzie można załadować zestawu w czasie wykonywania.

Ten błąd może wystąpić tylko wtedy, gdy edytujesz swoje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesty ręcznie; nie powinni obawiać ten błąd, jeśli Generowanie wdrożenie za pomocą programu Visual Studio.

## <a name="specify-individual-net-framework-assemblies-in-the-manifest"></a>Określ poszczególne zestawy .NET Framework w manifeście

Aplikacja nie będzie można załadować po zakończeniu edycji ręcznie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia, aby odwoływać się do starszej wersji [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] zestawu. Na przykład, jeśli dodaje odwołanie do zestawu przestrzeni nazw System.Net wersji [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] wcześniejszymi niż wersja określona w manifeście, następnie mógłby wystąpić błąd. Ogólnie rzecz biorąc, należy zrezygnować do określenia odniesienia do poszczególnych [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] zespołów, jak wersja [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] względem której działa aplikacja jest określony jako zależności w manifeście aplikacji.

## <a name="manifest-parsing-issues"></a>Manifest analizowania problemów

Pliki manifestu, które są używane przez [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] są plikami XML i musi być dobrze sformułowany i prawidłowy: muszą przestrzegać reguł dotyczących składni XML i składać się tylko elementy i atrybuty zdefiniowane w odpowiednich schematu XML.

Jest coś, co może powodować problemy w pliku manifestu wybierając nazwę aplikacji, który zawiera znaki specjalne, takie jak pojedyncze lub podwójne znaki cudzysłowu. Nazwa aplikacji jest częścią jego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tożsamości. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] obecnie nie analizuje tożsamości, które zawierają znaki specjalne. Jeśli aplikacja nie może aktywować, upewnij się, przy użyciu tylko alfabetycznej, cyfry dla nazwy i spróbować ponownie wdrażać.

Jeśli edytowano ręcznie swoje manifesty wdrożenia lub aplikacji, możesz mieć przypadkowo uszkodzony je. Uszkodzony manifest uniemożliwi poprawne [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instalacji. Możesz debugować takie błędy w czasie wykonywania, klikając **szczegóły** na **błąd ClickOnce** okno dialogowe, a także odczytu komunikat o błędzie w dzienniku. Dziennik się lista jedną z następujących komunikatów:

- Opis błąd składni i numer wiersza oraz znak położenie, w którym wystąpił błąd.

- Nazwa elementu lub atrybutu używanego w naruszenie schematu manifestu. XML zostały dodane do Twojego manifesty ręcznie, należy porównać swoje dodatki do schematów manifestu. Aby uzyskać więcej informacji, zobacz [manifest wdrażania ClickOnce](../deployment/clickonce-deployment-manifest.md) i [manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md).

- Wystąpi konflikt identyfikatorów. Odwołań do zależności w manifesty wdrażania i aplikacja muszą być unikatowe w obu ich `name` i `publicKeyToken` atrybutów. Jeśli oba atrybuty są zgodne między którychkolwiek dwóch elementów w obrębie manifestu, analizowania manifestu nie powiedzie się.

## <a name="precautions-when-manually-changing-manifests-or-applications"></a>Środki ostrożności, zmieniając ręcznie manifesty lub aplikacji

Podczas aktualizowania manifestu aplikacji, musisz ją ponownie podpisać manifest aplikacji i manifest wdrożenia. Manifest wdrożenia zawiera odwołanie do manifestu aplikacji, zawierający wartość skrótu tego pliku i jego podpis cyfrowy.

### <a name="precautions-with-deployment-provider-usage"></a>Środki ostrożności przy użyciu wdrożenia użycia dostawcy

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Manifest wdrożenia zawiera `deploymentProvider` właściwości, które wskazuje na pełną ścieżkę do lokalizacji, z którym zainstalowane i obsługiwanych aplikacji:

```xml
<deploymentProvider codebase="http://myserver/myapp.application" />
```

Ta ścieżka jest ustawiona, gdy [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tworzy aplikację i jest obowiązkowy w przypadku zainstalowanych aplikacji. Ścieżka wskazuje na lokalizację standardowa gdzie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Instalator zainstaluje aplikację i wyszukiwanie aktualizacji. Jeśli używasz **xcopy** polecenie, aby skopiować [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji do innej lokalizacji, ale nie należy zmieniać `deploymentProvider` właściwości [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] będą nadal odwoływały się ponownie do oryginalnej lokalizacji podczas próby pobrania aplikacja.

Jeśli chcesz przenieść lub kopiowania aplikacji, należy również zaktualizować `deploymentProvider` ścieżki, tak aby rzeczywiście instalacji klienta z nowej lokalizacji. Aktualizacja ta ścieżka jest przede wszystkim istotna, po zainstalowaniu aplikacji. Dla aplikacji online, które są zawsze uruchamiany za pośrednictwem oryginalny adres URL, ustawienie `deploymentProvider` jest opcjonalne. Jeśli `deploymentProvider` jest ustawiony, będą honorowane; w przeciwnym razie adres URL używany do uruchamiania aplikacji będzie służyć jako podstawowy adres URL do pobierania plików aplikacji.

> [!NOTE]
> Każdym zaktualizowanie manifestu należy również podpisać go ponownie.

## <a name="see-also"></a>Zobacz także

[Rozwiązywanie problemów z wdrożeniami ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
[aplikacji Securw ClickOnce](../deployment/securing-clickonce-applications.md)
[Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)