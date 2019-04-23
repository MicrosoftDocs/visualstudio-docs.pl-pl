---
title: Rozwiązywanie problemów z pakowaniem i wdrażaniem SharePoint | Dokumentacja firmy Microsoft
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- VSTO.WorkflowDeployment.Troubleshooting
- VS.SharePointTools.Project.PackageRetraction
- VS.SharePointTools.Deployment.Troubleshooting
- VS.SharePointTools.Deploying.Troubleshooting
- VS.SharePointTools.Project.DeploymentTroubleshooting
- VS.SharePointTools.Project.SharePointNotInstalled
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
- SharePoint development in Visual Studio, troubleshooting
- SharePoint development in Visual Studio, deployment conflict resolution
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0c949f9a5d8c56f44e0754715d056b4d3837f76a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60087602"
---
# <a name="troubleshoot-sharepoint-packaging-and-deployment"></a>Rozwiązywanie problemów z pakowaniem i wdrażaniem SharePoint
  W tym temacie omówiono różne problemy, które mogą wystąpić podczas pakowania i wdrażania rozwiązań programu SharePoint.

## <a name="enable-enhanced-debugging"></a>Włączanie ulepszonego debugowania
 Aby zdiagnozować między Visual Studio, SharePoint i innymi warstwami, klucza rejestru EnableDiagnostics służy do wyświetlania śladu stosu. Aby uzyskać więcej informacji, zobacz [rozwiązań SharePoint debugowania](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="add-project-output-to-the-solution-package"></a>Dodaj dane wyjściowe projektu do pakietu rozwiązań
 Dane wyjściowe projektu można dodać do pakietu przy użyciu projektanta pakietów. Jednak podczas dodawania danych wyjściowych projektu upewnij się, że platforma projektu odpowiada platformie rozwiązania SharePoint. Firma Microsoft zaleca użycie **dowolny Procesor** platformy docelowej dla zespołów, które mają zostać wdrożone na serwerze programu SharePoint. Aby uzyskać więcej informacji, zobacz [strona kompilowania, Projektant projektu &#40;języka Visual Basic&#41; ](../ide/reference/compile-page-project-designer-visual-basic.md) i [okno dialogowe Zaawansowane ustawienia kompilatora &#40;języka Visual Basic&#41;](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).

## <a name="validation-warnings-and-errors"></a>Walidacja ostrzeżeń i błędów
 Narzędzia projektowania programu SharePoint w programie Visual Studio wykonują czynności sprawdzania poprawności, aby sprawdzić, czy pakiet rozwiązania jest poprawnie uformowany. Można również utworzyć niestandardowe kroki sprawdzania poprawności dla pakietów i funkcji. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie funkcji niestandardowej oraz pakiet reguł sprawdzania poprawności dla rozwiązań SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

## <a name="deployment-conflict-resolution"></a>Rozwiązywanie konfliktów wdrażania
 Podczas wdrażania rozwiązania programu SharePoint, może wystąpić kolizja, gdy element na serwerze ma nazwę, adres URL lub identyfikator co element z pakietu rozwiązania. Możesz zmienić **Rozwiązywanie konfliktów wdrażania** właściwość, aby rozwiązać, zaraportować lub zignorować kolizje dla modułów, części sieci Web, przejrzenia listy wystąpień i typów zawartości.

 Poniższa tabela przedstawia ustawienia dla **Rozwiązywanie konfliktów wdrażania** właściwości.

|Wartość|Opis|
|-----------|-----------------|
|Automatyczne|Wykrywa kolizje i automatycznie rozwiązuje konflikty.|
|wiersz|Wykrywa kolizje i raportuje je do dewelopera przed rozwiązaniem konfliktów.|
|Brak|Nie wykrywa kolizji.|

## <a name="differences-between-f5-deployment"></a>Różnice między wdrożeniem F5
 Kiedy używasz [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] do wdrożenia projektu programu SharePoint do lokalnego serwera programu SharePoint do testowania i debugowania, istnieją pewne dodatkowe kroki są wykonywane przez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

1. Resetuj Internet Information Service (IIS) podczas wykonywania kroku wdrażania.

2. Automatycznie kojarzy przepływy pracy.

3. Ustaw kolejność aktywacji funkcji zgodnie z hierarchią w Projektancie pakietu.

   Możesz dodać kroki wdrażania niestandardowego do dalszych zmian **F5** zachowanie. Aby uzyskać więcej informacji, zobacz [instruktażu: Tworzenie niestandardowego kroku wdrożenia dla projektów programu SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="delay-displaying-sharepoint-page-when-deploy-visual-web-part"></a>Opóźnienie wyświetlania strony programu SharePoint podczas wdrażania wizualnego składnika web part
 Strony programu SharePoint wymaga dużo czasu, pojawiają się podczas wdrażania wizualnego składnika Web part do folderu Bin na [!INCLUDE[wiprlhext](../sharepoint/includes/wiprlhext-md.md)], [!INCLUDE[win7](../sharepoint/includes/win7-md.md)], lub [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)]. Jeśli zmienisz wszystkie pliki w najwyższego poziomu [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] następuje rekompilacja całej aplikacji sieci Web w katalogu, takiego jak katalog Bin. Może to spowodować opóźnienie maksymalnie 25 sekund dla strony programu SharePoint do renderowania.

### <a name="error-message"></a>Komunikat o błędzie
 Brak.

### <a name="resolution"></a>Rozwiązanie
 Aby obejść ten problem, wykonaj następujące czynności:

1. Zainstaluj aktualizację KB967535, zgodnie z opisem w artykule firmy Microsoft Support [NAPRAW: Poprawka jest dostępna rozwiązać dwa problemy w programie ASP.NET przez usługi IIS 7.0, Windows Vista i Windows Server 2008](http://go.microsoft.com/fwlink/?LinkId=179055).

2. Dodaj następujący wiersz do pliku Web.config:

    ```xml
    <compilation batch="false" optimizeCompilations="true">
    ```

## <a name="sharepoint-project-deployment-fails-with-error-failed-to-extract-the-cab-file-in-the-solution"></a>Wdrażanie projektu programu SharePoint kończy się niepowodzeniem z powodu błędu "Nie można wyodrębnić pliku cab w rozwiązaniu"
 Jeśli nazwa dowolnego elementu projektu programu SharePoint zawiera nawiasy, rozwiązania kończy się niepowodzeniem wdrożenia z powodu błędu.

### <a name="error-message"></a>Komunikat o błędzie
 Wystąpił błąd podczas kroku wdrażania "Dodaj rozwiązanie": Nie można wyodrębnić pliku cab w rozwiązaniu.

### <a name="resolution"></a>Rozwiązanie
 Aby obejść ten problem, należy usunąć wszelkie nawiasy w nazwach elementów projektu programu SharePoint.

## <a name="error-appears-when-deploying-a-visual-web-part-to-a-site-on-a-different-web-application"></a>Błąd pojawia się podczas wdrażania wizualnego składnika web part do witryny innej aplikacji sieci web
 Przy pierwszym wdrożeniu wizualny składnik Web part do witryny aplikacji sieci Web innej niż ta, na którym jest aktualnie wdrożony (przez zmianę właściwości SiteUrl wizualnego składnika Web part), wystąpi błąd.

### <a name="error-message"></a>Komunikat o błędzie
 Wystąpił błąd podczas kroku wdrażania "Dodaj rozwiązanie": Funkcja o identyfikatorze [#] został już zainstalowany w tej farmie. Użyj atrybutu force, aby jawnie ponownie zainstalować tę funkcję.

### <a name="resolution"></a>Rozwiązanie
 Ten błąd występuje ze względu na sposób, w jaki funkcje programu visual Web part jest wycofana w programie SharePoint. Aby pomyślnie wdrożyć wizualny składnik Web part, należy ponownie wdrożyć rozwiązanie, wybierając **F5** klucza.

## <a name="warning-appears-when-deploying-nested-user-controls"></a>Ostrzeżenie pojawia się podczas wdrażania zagnieżdżonych formantów użytkownika
 Ostrzeżenie to pojawia się podczas wdrażania rozwiązania programu SharePoint, które ma zagnieżdżone formanty użytkownika, takie jak wizualny składnik Web part, który zawiera formant użytkownika lub formant użytkownika, który zawiera wizualny składnik Web part lub inny formant użytkownika. Ostrzeżenie to pojawia się, czy dodajesz formant do projektanta, przeciągając go z przybornika lub przy użyciu @Register dyrektywy w widoku źródła.

### <a name="error-message"></a>Komunikat o błędzie
 Ostrzeżenie 1 Element ' [*nazwa kontrolki*] "nie jest znanym elementem. Może to wystąpić, jeśli wystąpi błąd kompilacji w witrynie sieci Web, lub brakuje pliku web.config.

### <a name="resolution"></a>Rozwiązanie
 Jeśli [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] system projektu nie ma informacji o zagnieżdżonego formantu użytkownika, nie może dostarczyć IntelliSense i emituje ostrzeżenie. System projektu nie rozpoznaje zagnieżdżonego formantu użytkownika jeśli projekt jest kompilowany, a projektant nie jest zamknięty i ponownie otwarty lub wycofać automatycznie opcja jest włączona, co powoduje, że formant użytkownika ma zostać wycofany z gałęzi programu SharePoint po debugowaniu.

 Aby usunąć to ostrzeżenie, skompiluj projekt i następnie zamknij i ponownie otwórz projektanta lub wyłącz automatyczne wycofanie opcji dla projektu. Aby to zrobić, należy wyczyścić **automatycznie Wycofaj po debugowaniu** pole wyboru na **SharePoint** karty w oknie dialogowym właściwości projektu.

## <a name="see-also"></a>Zobacz także

- [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)