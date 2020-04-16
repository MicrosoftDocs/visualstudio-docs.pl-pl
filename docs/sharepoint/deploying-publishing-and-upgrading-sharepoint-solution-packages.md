---
title: Wdrażanie, publikowanie, uaktualnianie & uaktualniania pakietów rozwiązań programu SharePoint
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SharePointProjectPropertyTab
- VS.SharePointTools.Project.Publishing
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d8e55b01173e749395f60d189366a08907bdaccd
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444973"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>Wdrażanie, publikowanie i uaktualnianie pakietów rozwiązań programu SharePoint
  Po opracowaniu rozwiązania programu SharePoint w programie Visual Studio można wdrożyć jego plik pakietu (wsp) na lokalnym serwerze programu SharePoint lub opublikować go na zdalnym lub lokalnym serwerze programu SharePoint. W przypadku wdrażania plików można dostosować sposób wdrażania plików pakietów (wsp).

> [!NOTE]
> Obecnie tylko rozwiązania w trybie piaskownicy mogą być publikowane na zdalnych serwerach programu SharePoint. Aby uzyskać więcej informacji, zobacz [Zagadnienia dotyczące rozwiązania w trybie piaskownicy](../sharepoint/sandboxed-solution-considerations.md).

## <a name="deploy-publish-and-upgrade"></a>Wdrażanie, publikowanie i uaktualnianie
 *Wdrażanie* odnosi się do kopiowania pliku rozwiązania programu SharePoint utworzonego z projektu programu SharePoint w programie Visual Studio do hosta lokalnego. W wdrożonym rozwiązaniu można skonfigurować kroki wdrażania, takie jak recykling puli internetowych usług informacyjnych (IIS), aktywowanie rozwiązania po wdrożeniu i tak dalej. Aby wdrożyć, użyj polecenia **Wdrażanie** w menu **Kompilacja.** Aby uzyskać więcej informacji, zobacz [Jak: Edytowanie konfiguracji wdrożenia programu SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) i [jak: Wdrażanie i publikowanie rozwiązania programu SharePoint w lokalnej witrynie programu SharePoint](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 *Publikowanie* odnosi się do przekazywania pliku rozwiązania programu SharePoint w trybie piaskownicy do zdalnej witryny programu SharePoint; oznacza to, że witryna znajduje się w innym systemie. Można również opublikować plik rozwiązania w trybie piaskownicy programu SharePoint w lokalnej witrynie programu SharePoint, ale niezależnie od tego, czy witryna opublikowana jest lokalna, czy zdalna, nie można skonfigurować jej kroków wdrażania.

 *Uaktualnianie* odnosi się do aktualizowania istniejącego zdalnie lub lokalnie opublikowanego rozwiązania programu SharePoint. Po wniesieniu jakichkolwiek zmian do rozwiązania programu SharePoint w programie Visual Studio, należy zmienić nazwę pliku pakietu rozwiązania, ponownie opublikować rozwiązanie, a następnie uaktualnić rozwiązanie po pomyślnym opublikowaniu. Jeśli ponownie opublikujesz rozwiązanie opublikowane lokalnie, możesz zastąpić istniejący plik rozwiązania.

## <a name="deploy-packages"></a>Wdrażanie pakietów
 Pliki pakietów można wdrożyć na serwerze programu SharePoint na komputerze deweloperskim w celu testowania i debugowania. Można również utworzyć plik pakietu, który można zainstalować na innym komputerze, wybierając przycisk opcji **Publikuj w systemie plików** w oknie dialogowym **Publikowanie.** Pakiet jest tworzony i kopiowany do określonej ścieżki pliku lokalnego. Aby wdrożyć rozwiązanie programu SharePoint na serwerze lokalnym, użyj polecenia **Wdrażanie** w menu **Kompilacja.** Aby uzyskać więcej informacji, zobacz [Jak: Wdrażanie i publikowanie rozwiązania programu SharePoint w lokalnej witrynie programu SharePoint](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 Aby dowiedzieć się, jak wdrożyć definicję listy, dodać odbiornik zdarzeń i użyć Projektanta funkcji i Projektanta pakietów, zobacz [Przewodnik: Wdrażanie definicji listy zadań projektu](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md).

## <a name="customize-the-deployment-process"></a>Dostosowywanie procesu wdrażania
 W poniższej tabeli przedstawiono dwie konfiguracje wdrażania, których można użyć podczas debugowania i wdrażania rozwiązania programu SharePoint.

|Konfiguracja wdrażania|Opis|
|------------------------------|-----------------|
|Domyślne|Domyślna konfiguracja wdrażania. Wykonywane są następujące kroki wdrażania:<br /><br /> 1. Uruchom polecenie przed wdrożeniem.<br />2. Recykling puli aplikacji usług IIS.<br />3. Wycofać roztwór.<br />4. Dodać rozwiązanie.<br />5. Aktywuj funkcje.<br />6. Uruchom polecenie po wdrożeniu.<br /><br /> Po odinstalowaniu pakietu wykonywane są następujące kroki wycofywania.<br /><br /> 1. Recykling puli aplikacji usług IIS.<br />2. Wycofać roztwór.|
|Brak aktywacji|Ta konfiguracja wdrażania uruchamia te same kroki co konfiguracja domyślna, ale pomija krok aktywacji.|

 Można utworzyć własne konfiguracje wdrażania, aby wykonać jeden krok lub zmienić kolejność kroków w procesie wdrażania. Aby uzyskać więcej informacji, zobacz [Jak: Edytowanie konfiguracji wdrożenia programu SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

 Można również dodać polecenia do uruchomienia przed i po wdrożeniu. Aby uzyskać więcej informacji, zobacz [Jak: Ustawianie poleceń wdrażania programu SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).

## <a name="publish-packages-to-a-remote-or-local-server"></a>Publikowanie pakietów na serwerze zdalnym lub lokalnym
 Aby opublikować rozwiązanie programu SharePoint w trybie piaskownicy na serwerze zdalnym, na pasku menu wybierz polecenie **Buduj**, **Publikuj**, `https://someremoteserver.sharepoint.microsoftonline.com`a następnie w oknie dialogowym **Publikowanie** wybierz przycisk opcji **Publikuj w witrynie programu SharePoint,** podając adres URL serwera zdalnego, na przykład .

 Aby opublikować rozwiązanie programu SharePoint na serwerze lokalnym, w oknie dialogowym **Publikowanie** wybierz przycisk opcji **Publikuj w systemie plików,** udostępniając lokalną ścieżkę systemową.

 Po pomyślnym opublikowaniu rozwiązania w programie SharePoint rozwiązanie pojawi się w **Galerii rozwiązań,** w której można je aktywować. Aby uzyskać więcej informacji, zobacz [Jak: Wdrażanie, publikowanie i uaktualnianie rozwiązań programu SharePoint na serwerze zdalnym](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

### <a name="upgrade-published-packages"></a>Uaktualnianie opublikowanych pakietów
 Jeśli po opublikowaniu zostanie wprowadzone zmiany w projekcie programu SharePoint w programie Visual Studio, opublikowany pakiet musi zostać uaktualniony w celu uwzględnienia zmian. Aby uaktualnienie zostało pomyślnie uaktualnione, pakiet musi mieć unikatową nazwę. Jeśli pakiet o tej samej nazwie zostanie znaleziony w witrynie programu SharePoint — co może wystąpić podczas aktualizowania istniejącej aplikacji — błąd ostrzega o konflikcie nazwy pliku i umożliwia zmianę nazwy pakietu. Po ponownym opublikowaniu nowy pakiet pojawi się w witrynie programu SharePoint i można go uaktualnić. Uaktualniony pakiet aktualizuje rozwiązanie przy użyciu danych ze starszego pakietu, a następnie aktywuje rozwiązanie w programie SharePoint. Aby uzyskać więcej informacji, zobacz [Jak: Wdrażanie, publikowanie i uaktualnianie rozwiązań programu SharePoint na serwerze zdalnym](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

## <a name="see-also"></a>Zobacz też
- [Pakowanie i wdrażanie rozwiązań programu SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
