---
title: Rozwiązywanie problemów z pakietami i wdrażaniem programu SharePoint | Microsoft Docs
description: Zrozumienie i rozwiązywanie różnych problemów, które mogą wystąpić podczas pakowania i wdrażania rozwiązań programu SharePoint.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 07ce649a22573041768bfc316f65bfcdf7577b98
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2020
ms.locfileid: "95969942"
---
# <a name="troubleshoot-sharepoint-packaging-and-deployment"></a>Rozwiązywanie problemów z pakietami i wdrażaniem programu SharePoint
  W tym temacie omówiono różne problemy, które mogą wystąpić podczas pakowania i wdrażania rozwiązań programu SharePoint.

## <a name="enable-enhanced-debugging"></a>Włącz ulepszone debugowanie
 Aby zdiagnozować między programem Visual Studio, SharePoint i innymi warstwami, można użyć klucza rejestru EnableDiagnostics do wyświetlania śladu stosu. Aby uzyskać więcej informacji, zobacz [Debugowanie rozwiązań programu SharePoint](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="add-project-output-to-the-solution-package"></a>Dodawanie danych wyjściowych projektu do pakietu rozwiązania
 Dane wyjściowe projektu można dodać do pakietu za pomocą projektanta pakietów. Jednak podczas dodawania danych wyjściowych projektu upewnij się, że platforma projektu jest zgodna z platformą rozwiązania SharePoint. Zalecamy używanie dowolnego celu platformy **procesora CPU** dla zestawów, które mają zostać wdrożone na serwerze programu SharePoint. Aby uzyskać więcej informacji, zobacz [stronę Kompilacja, Projektant projektu &#40;Visual Basic&#41;](../ide/reference/compile-page-project-designer-visual-basic.md) i [Zaawansowane ustawienia kompilatora okno dialogowe &#40;Visual Basic&#41;](../ide/reference/advanced-compiler-settings-dialog-box-visual-basic.md).

## <a name="validation-warnings-and-errors"></a>Ostrzeżenia i błędy walidacji
 Narzędzia deweloperskie programu SharePoint w programie Visual Studio wykonują kroki weryfikacji, aby sprawdzić, czy pakiet rozwiązania został poprawnie sformatowany. Możesz również utworzyć niestandardowe kroki walidacji dla swoich funkcji i pakietów. Aby uzyskać więcej informacji, zobacz [How to: Create Custom Feature and Package Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

## <a name="deployment-conflict-resolution"></a>Rozwiązywanie konfliktów wdrożenia
 Po wdrożeniu rozwiązania programu SharePoint może wystąpić konflikty, gdy element na serwerze ma taką samą nazwę, adres URL lub identyfikator co element w pakiecie rozwiązania. Można zmienić właściwość **rozwiązywania konfliktów wdrażania** , aby rozwiązać, zgłosić lub zignorować kolizje dla modułów, składników Web Part, wystąpień list i typów zawartości.

 W poniższej tabeli przedstawiono ustawienia właściwości **Rozwiązywanie konfliktów wdrażania** .

|Wartość|Opis|
|-----------|-----------------|
|Automatyczny|Wykrywa kolizje i automatycznie rozwiązuje konflikty.|
|Monit|Wykrywa kolizje i przekazuje je deweloperom przed rozpuszczeniem konfliktów.|
|Brak|Nie wykrywa kolizji.|

## <a name="differences-between-f5-deployment"></a>Różnice między wdrożeniem F5
 W przypadku używania programu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] do wdrażania projektu programu SharePoint na lokalnym serwerze SharePoint do testowania i debugowania należy wykonać kilka dodatkowych kroków, które są wykonywane przez program [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

1. Zresetuj Internet Information Service (IIS) podczas kroku wdrożenia.

2. Automatycznie Skojarz przepływy pracy.

3. Ustaw kolejność aktywacji funkcji zgodnie z hierarchią w projektancie pakietów.

   Możesz dodać niestandardowe kroki wdrażania, aby zmienić zachowanie **F5** . Aby uzyskać więcej informacji, zobacz [Przewodnik: Tworzenie niestandardowego kroku wdrożenia dla projektów programu SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="delay-displaying-sharepoint-page-when-deploy-visual-web-part"></a>Opóźnienie wyświetlania strony programu SharePoint podczas wdrażania wizualnego składnika Web Part
 Podczas wdrażania wizualnego składnika Web Part do folderu bin w systemie, [!INCLUDE[wiprlhext](../sharepoint/includes/wiprlhext-md.md)] [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] lub [!INCLUDE[winsvr08](../sharepoint/includes/winsvr08-md.md)] . W przypadku zmiany plików w katalogu najwyższego poziomu [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] , takich jak katalog bin, cała aplikacja sieci Web zostanie ponownie skompilowana. Może to spowodować opóźnienie do 25 sekund, aby można było renderować stronę programu SharePoint.

### <a name="error-message"></a>Komunikat o błędzie
 Brak.

### <a name="resolution"></a>Rozwiązanie
 Aby obejść ten problem, wykonaj następujące czynności:

1. Zainstaluj aktualizację KB967535, zgodnie z opisem w artykule Naprawa artykułu pomoc techniczna firmy Microsoft [: poprawka jest dostępna do rozwiązywania dwóch problemów w programie ASP.NET w usługach IIS 7,0 dla systemów Windows Vista i Windows Server 2008](https://support.microsoft.com/help/967535).

2. Dodaj następujący wiersz do pliku Web.config:

    ```xml
    <compilation batch="false" optimizeCompilations="true">
    ```

## <a name="sharepoint-project-deployment-fails-with-error-failed-to-extract-the-cab-file-in-the-solution"></a>Wdrożenie projektu programu SharePoint kończy się niepowodzeniem z powodu błędu "nie można wyodrębnić pliku cab w rozwiązaniu"
 Jeśli nazwa dowolnego elementu projektu programu SharePoint zawiera nawiasy, jego rozwiązanie kończy się niepowodzeniem po wystąpieniu błędu.

### <a name="error-message"></a>Komunikat o błędzie
 Wystąpił błąd w kroku wdrożenia "Dodaj rozwiązanie": nie można wyodrębnić pliku cab w rozwiązaniu.

### <a name="resolution"></a>Rozwiązanie
 Aby obejść ten problem, Usuń wszystkie nawiasy w nazwach elementów projektu programu SharePoint.

## <a name="error-appears-when-deploying-a-visual-web-part-to-a-site-on-a-different-web-application"></a>Błąd pojawia się podczas wdrażania wizualnego składnika Web Part do witryny w innej aplikacji sieci Web
 Przy pierwszym wdrożeniu wizualnego składnika Web Part do witryny w aplikacji sieci Web innej niż ta, na której jest aktualnie wdrożona (poprzez zmianę właściwości SiteUrl w składniku Web Part), pojawia się błąd.

### <a name="error-message"></a>Komunikat o błędzie
 Wystąpił błąd w kroku wdrożenia "Dodaj rozwiązanie": funkcja o IDENTYFIKATORze [#] została już zainstalowana w tej farmie. Użyj atrybutu Force, aby jawnie ponownie zainstalować funkcję.

### <a name="resolution"></a>Rozwiązanie
 Ten błąd występuje ze względu na sposób wycofywania funkcji wizualnego składnika Web Part w programie SharePoint. Aby pomyślnie wdrożyć wizualny składnik Web Part, wdróż rozwiązanie ponownie, wybierając klawisz **F5** .

## <a name="warning-appears-when-deploying-nested-user-controls"></a>Ostrzeżenie pojawia się podczas wdrażania zagnieżdżonych formantów użytkownika
 To ostrzeżenie występuje, gdy wdrażasz rozwiązanie SharePoint z zagnieżdżonymi kontrolkami użytkownika, takimi jak wizualny składnik Web Part, który zawiera kontrolkę użytkownika lub kontrolkę użytkownika, która zawiera wizualny składnik Web Part lub inną kontrolkę użytkownika. To ostrzeżenie jest wykonywane niezależnie od tego, czy dodajesz formant do projektanta, przeciągając go z przybornika, czy za pomocą @Register dyrektywy w widoku źródło.

### <a name="error-message"></a>Komunikat o błędzie
 Ostrzeżenie 1 element ' [*Nazwa formantu*] ' nie jest znanym elementem. Taka sytuacja może wystąpić, jeśli wystąpi błąd kompilacji w witrynie sieci Web lub brak pliku web.config.

### <a name="resolution"></a>Rozwiązanie
 Jeśli [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] system projektu nie jest świadomy zagnieżdżonej kontrolki użytkownika, nie może dostarczyć funkcji IntelliSense i emituje ostrzeżenie. System projektu jest nieświadomy zagnieżdżonej kontrolki użytkownika, jeśli projekt nie został skompilowany i projektant nie zostanie zamknięty i ponownie otwarty, lub jeśli włączono opcję autowycofywania, co powoduje, że kontrolka użytkownika zostanie wycofana z gałęzi programu SharePoint po debugowaniu.

 Aby usunąć to ostrzeżenie, Skompiluj projekt, a następnie zamknij i ponownie otwórz projektanta lub wyłącz opcję autowycofywania dla projektu. W tym celu wyczyść pole wyboru **autowycofywanie po debugowaniu** na karcie **SharePoint** w oknie dialogowym właściwości projektu.

## <a name="see-also"></a>Zobacz też

- [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)