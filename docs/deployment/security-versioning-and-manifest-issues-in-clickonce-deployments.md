---
title: Zabezpieczenia/przechowywanie wersji/problemy z manifestem (ClickOnce)
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 881a0f9d5062e335fb7e03653bde11e032f89aca
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90811250"
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>Zabezpieczenia, przechowywanie wersji i problemy z manifestami we wdrożeniach technologii ClickOnce

Istnieje wiele problemów z [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zabezpieczeniami, przechowywaniem wersji aplikacji i składnią manifestu oraz semantyką, które mogą spowodować, że [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenie nie powiedzie się.

## <a name="clickonce-and-windows-vista-user-account-control"></a>Kontrola konta użytkownika ClickOnce i systemu Windows Vista

W programie [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] aplikacje domyślnie działają jako użytkownicy standardowi, nawet jeśli bieżący użytkownik jest zalogowany przy użyciu konta z uprawnieniami administratora. Jeśli aplikacja musi wykonać akcję, która wymaga uprawnień administratora, instruuje system operacyjny, który następnie monituje użytkownika o wprowadzenie poświadczeń administratora. Ta funkcja, która nosi nazwę Kontrola konta użytkownika (UAC), uniemożliwia aplikacjom wprowadzanie zmian, które mogą wpływać na cały system operacyjny bez jawnej zgody użytkownika. Aplikacje systemu Windows deklarują, że wymagają one podniesienia uprawnień przez określenie `requestedExecutionLevel` atrybutu w `trustInfo` sekcji ich manifestu aplikacji.

Ze względu na ryzyko ujawnienia aplikacji przed atakami w celu podniesienia poziomu zabezpieczeń [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje nie mogą żądać podniesienia uprawnień, jeśli kontrola konta użytkownika jest włączona dla klienta. Wszystkie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje, które próbują ustawić jej `requestedExecutionLevel` atrybut na `requireAdministrator` lub `highestAvailable` nie będą instalowane w systemie [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] .

W niektórych przypadkach [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja może próbować uruchomić z uprawnieniami administratora z powodu logiki wykrywania Instalatora w systemie [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)] . W takim przypadku można ustawić `requestedExecutionLevel` atrybut w manifeście aplikacji na `asInvoker` . Spowoduje to, że aplikacja zostanie uruchomiona bez podniesienia uprawnień. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] automatycznie dodaje ten atrybut do wszystkich manifestów aplikacji.

Jeśli tworzysz aplikację, która wymaga uprawnień administratora przez cały okres istnienia aplikacji, należy rozważyć wdrożenie aplikacji przy użyciu technologii Instalator Windows (MSI). Aby uzyskać więcej informacji, zobacz [podstawy Instalator Windows](../extensibility/internals/windows-installer-basics.md).

## <a name="online-application-quotas-and-partial-trust-applications"></a>Przydziały aplikacji online i częściowo zaufane aplikacje

Jeśli [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja jest uruchamiana w trybie online, a nie za pomocą instalacji, musi być zgodna z limitem przydziału dla aplikacji online. Ponadto aplikacja sieciowa, która działa w częściowej relacji zaufania, na przykład z ograniczonym zestawem uprawnień zabezpieczeń, nie może być większa niż połowa rozmiaru przydziału.

Aby uzyskać więcej informacji, i instrukcje dotyczące zmiany limitu przydziału aplikacji online, zobacz [Omówienie pamięci podręcznej ClickOnce](../deployment/clickonce-cache-overview.md).

## <a name="versioning-issues"></a>Problemy z przechowywaniem wersji

W przypadku przypisywania silnych nazw do zestawu i zwiększenia numeru wersji zestawu w celu odzwierciedlenia aktualizacji aplikacji mogą wystąpić problemy. Wszystkie zestawy skompilowane z odwołaniem do zestawu o silnej nazwie muszą zostać ponownie skompilowane lub zestaw będzie próbować odwoływać się do starszej wersji. Zestaw podejmie próbę, ponieważ zestaw używa starej wartości wersji w żądaniu powiązania.

Załóżmy na przykład, że masz zestaw o silnej nazwie we własnym projekcie w wersji 1.0.0.0. Po skompilowaniu zestawu należy dodać go jako odwołanie do projektu, który zawiera główną aplikację. W przypadku aktualizacji zestawu Zwiększ wersję do 1.0.0.1, a następnie spróbuj wdrożyć ją bez również ponownego kompilowania aplikacji, aplikacja nie będzie mogła załadować zestawu w czasie wykonywania.

Ten błąd może wystąpić tylko w przypadku [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ręcznego edytowania manifestów; ten błąd nie powinien wystąpić w przypadku wygenerowania wdrożenia przy użyciu programu Visual Studio.

## <a name="specify-individual-net-framework-assemblies-in-the-manifest"></a>Określ poszczególne zestawy .NET Framework w manifeście

Nie można załadować aplikacji, jeśli zostało ręcznie edytowane [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenie w celu odwołującego się do starszej wersji zestawu .NET Framework. Na przykład, jeśli dodano odwołanie do zestawu System.Net dla wersji .NET Framework przed wersją określoną w manifeście, wystąpi błąd. Ogólnie rzecz biorąc nie należy próbować określać odwołań do poszczególnych zestawów .NET Framework, ponieważ wersja .NET Framework, względem której działa aplikacja, jest określona jako zależność w manifeście aplikacji.

## <a name="manifest-parsing-issues"></a>Problemy z analizowaniem manifestu

Pliki manifestu, które są używane przez [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pliki XML, muszą być zarówno dobrze sformułowane, jak i prawidłowe: muszą przestrzegać reguł SKŁADNI XML i używać tylko elementów i atrybutów zdefiniowanych w odpowiednim schemacie XML.

Coś, co może spowodować problemy w pliku manifestu, wybiera nazwę aplikacji, która zawiera znak specjalny, taki jak pojedynczy lub podwójny cudzysłów. Nazwa aplikacji jest częścią swojej [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tożsamości. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] obecnie nie są analizowane tożsamości, które zawierają znaki specjalne. Jeśli nie można uaktywnić aplikacji, upewnij się, że używasz tylko znaków alfabetycznych i liczbowych, a następnie ponów próbę wdrożenia.

Jeśli ręcznie edytowano manifesty wdrożenia lub aplikacji, może to spowodować ich przypadkowe uszkodzenie. Uszkodzony manifest uniemożliwi poprawność [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] instalacji. Można debugować takie błędy w czasie wykonywania, klikając pozycję **szczegóły** w oknie dialogowym **Błąd ClickOnce** i odczytując komunikat o błędzie w dzienniku. Dziennik wyświetli jeden z następujących komunikatów:

- Opis błędu składniowy oraz numer wiersza i pozycja znaku, w których wystąpił błąd.

- Nazwa elementu lub atrybutu używanego do naruszenia schematu manifestu. Jeśli kod XML został dodany ręcznie do manifestów, trzeba będzie porównać Dodatki do schematów manifestu. Aby uzyskać więcej informacji, zobacz [manifest wdrożenia ClickOnce](../deployment/clickonce-deployment-manifest.md) i [manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md).

- Konflikt identyfikatorów. Odwołania do zależności w manifestach wdrożenia i aplikacji muszą być unikatowe w obu `name` `publicKeyToken` atrybutach i. Jeśli oba atrybuty pasują do któregokolwiek z dwóch elementów w manifeście, analiza manifestu nie powiedzie się.

## <a name="precautions-when-manually-changing-manifests-or-applications"></a>Środki ostrożności podczas ręcznego zmieniania manifestów lub aplikacji

Podczas aktualizowania manifestu aplikacji należy ponowne podpisać manifest aplikacji i manifest wdrożenia. Manifest wdrożenia zawiera odwołanie do manifestu aplikacji, który zawiera skrót do tego pliku i jego podpis cyfrowy.

### <a name="precautions-with-deployment-provider-usage"></a>Środki ostrożności dotyczące użycia dostawcy wdrożenia

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Manifest wdrożenia ma `deploymentProvider` Właściwość, która wskazuje pełną ścieżkę lokalizacji, w której aplikacja powinna być zainstalowana i serwisowana:

```xml
<deploymentProvider codebase="http://myserver/myapp.application" />
```

Ta ścieżka jest ustawiana podczas [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tworzenia aplikacji i jest obowiązkowa dla zainstalowanych aplikacji. Ścieżka wskazuje lokalizację standardową, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] z której Instalator zainstaluje aplikację, a następnie wyszukuje aktualizacje. Jeśli używasz polecenia **xcopy** do kopiowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji do innej lokalizacji, ale nie zmieniaj `deploymentProvider` właściwości, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] będzie ona nadal odwoływać się do oryginalnej lokalizacji podczas próby pobrania aplikacji.

Jeśli chcesz przenieść lub skopiować aplikację, należy również zaktualizować `deploymentProvider` ścieżkę, aby klient rzeczywiście instalował z nowej lokalizacji. Aktualizacja tej ścieżki jest głównie istotna, jeśli masz zainstalowane aplikacje. W przypadku aplikacji online, które są zawsze uruchamiane przy użyciu oryginalnego adresu URL, ustawienie `deploymentProvider` jest opcjonalne. Jeśli `deploymentProvider` jest ustawiona, zostanie ona zastosowana; w przeciwnym razie adres URL służący do uruchamiania aplikacji będzie używany jako podstawowy adres URL pobierania plików aplikacji.

> [!NOTE]
> Za każdym razem, gdy aktualizujesz manifest, należy również podpisać go ponownie.

## <a name="see-also"></a>Zobacz też

[Rozwiązywanie problemów z wdrożeniami ClickOnce](../deployment/troubleshooting-clickonce-deployments.md) 
 [Bezpieczne aplikacje ClickOnce](../deployment/securing-clickonce-applications.md) 
 [Wybierz strategię wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
