---
title: Wdrażanie, publikowanie i aktualizowanie pakietów rozwiązania SharePoint | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: a49ad82cc6cbb2eef8a8746b2c94575925ab1ddd
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436736"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>Wdrażanie, publikowanie oraz aktualizowanie pakietów rozwiązania SharePoint
  Po opracowywania rozwiązania programu SharePoint w programie Visual Studio, możesz wdrożyć jego pliku pakietu (wsp) na lokalnym serwerze programu SharePoint lub opublikować ją w lokalnym lub zdalnym serwerem programu SharePoint. Jeśli pliki są wdrożone, można dostosować, jak wdrożonych plików pakietu (wsp).

> [!NOTE]
> Obecnie tylko rozwiązania w trybie piaskownicy mogą być publikowane do serwerów zdalnych programu SharePoint. Aby uzyskać więcej informacji, zobacz [uwagi dotyczące rozwiązania typu piaskownica](../sharepoint/sandboxed-solution-considerations.md).

## <a name="deploy-publish-and-upgrade"></a>Wdrażanie, publikowanie oraz aktualizowanie
 *Wdrażanie* odwołuje się do kopiowania pliku rozwiązania programu SharePoint, utworzony na podstawie projektu programu SharePoint w programie Visual Studio do hosta lokalnego. W wdrożonym rozwiązaniem należy skonfigurować kroków wdrażania, takie jak odtwarzanie puli usług Internet Information Services (IIS), aktywowanie rozwiązania po wdrożeniu i tak dalej. Aby wdrożyć, użyj **Wdróż** polecenie **kompilacji** menu. Aby uzyskać więcej informacji, zobacz [jak: Edytowanie konfiguracji wdrażania SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) i [jak: Wdrażanie oraz publikowanie rozwiązania SharePoint w witrynie programu SharePoint w lokalnej](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 *Publikowanie* odwołuje się do przekazania plik piaskownicy rozwiązań programu SharePoint do zdalnego programu SharePoint site, czyli znajduje się w innym systemie lokacji. Możesz również opublikować plik rozwiązania w trybie piaskownicy programu SharePoint w lokalnej witrynie programu SharePoint, ale niezależnie od tego, czy lokacji publikowane w lokalnym lub zdalnym, nie można skonfigurować jej kroki związane z wdrażaniem.

 *Uaktualnianie* odwołuje się do aktualizowania istniejącego zdalne lub lokalne opublikowane rozwiązania programu SharePoint. Po wszelkie zmiany zostaną wprowadzone do rozwiązania programu SharePoint w programie Visual Studio, możesz zmienić nazwę pliku pakietu rozwiązania, ponownie opublikować rozwiązanie, a następnie Uaktualnij rozwiązania po pomyślnym publikuje ponownie. Jeśli ponownie opublikować opublikowanych lokalnie rozwiązania może spowodować zastąpienie istniejącego pliku rozwiązania.

## <a name="deploy-packages"></a>Wdrażanie pakietów
 Pliki pakietu programu SharePoint server można wdrożyć na komputerze deweloperskim do testowania i debugowania. Można również utworzyć plik pakietu, który można zainstalować na innym komputerze, wybierając **opublikowanie w systemie plików** przycisków opcji w **Publikuj** okno dialogowe. Pakiet jest utworzony i skopiowany do ścieżkę do określonego pliku lokalnego. Aby wdrożyć rozwiązania programu SharePoint na serwerze lokalnym, użyj **Wdróż** polecenie **kompilacji** menu. Aby uzyskać więcej informacji, zobacz [jak: Wdrażanie oraz publikowanie rozwiązania SharePoint w lokalnej witrynie SharePoint](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 Aby dowiedzieć się, jak wdrażanie definicji listy, dodawania odbiorców zdarzenia i korzystać z projektanta funkcji i projektancie pakietu, zobacz [instruktażu: Wdrażanie definicji listy zadań projektu](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md).

## <a name="customize-the-deployment-process"></a>Dostosowywanie procesu wdrażania
 W poniższej tabeli przedstawiono z dwiema konfiguracjami wdrożenia używanych podczas debugowania i wdrażania rozwiązania programu SharePoint.

|Konfiguracja wdrożenia|Opis|
|------------------------------|-----------------|
|Domyślny|Domyślna konfiguracja wdrożenia. Wykonywane są następujące wdrożenia:<br /><br /> 1.  Wykonywanie polecenia przed wdrożeniem.<br />2.  Odtwórz pulę aplikacji usług IIS.<br />3.  Wycofaj rozwiązanie.<br />4.  Dodaj rozwiązanie.<br />5.  Aktywacja funkcji.<br />6.  Wykonywanie polecenia po wdrożeniu.<br /><br /> Po odinstalowaniu pakietu są wykonywane następujące kroki wycofywania.<br /><br /> 1.  Odtwórz pulę aplikacji usług IIS.<br />2.  Wycofaj rozwiązanie.|
|Nie aktywacji|Tej konfiguracji wdrożenia jest uruchamiane te same kroki jako konfiguracji domyślnej, ale pomija krok aktywacji.|

 Możesz tworzyć własne konfiguracje wdrożenia na ukończenie jednego kroku lub zmiana kolejności kroków w procesie wdrażania. Aby uzyskać więcej informacji, zobacz [jak: Edytowanie konfiguracji wdrażania SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

 Można również dodać polecenia do uruchomienia przed i po wdrożeniu. Aby uzyskać więcej informacji, zobacz [jak: Ustawianie poleceń wdrażania SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).

## <a name="publish-packages-to-a-remote-or-local-server"></a>Publikowanie pakietów na serwerze lokalnym lub zdalnym
 Aby opublikować rozwiązanie w trybie piaskownicy programu SharePoint na serwerze zdalnym, na pasku menu wybierz **kompilacji**, **Publikuj**, a następnie w **Publikuj** okna dialogowego wybierz **Publikowania w witrynie SharePoint** przycisk opcji, podając adres URL serwera zdalnego, takich jak **https://someremoteserver.sharepoint.microsoftonline.com**.

 Publikowanie rozwiązania SharePoint na serwerze lokalnym, w **Publikuj** okna dialogowego wybierz **opublikowanie w systemie plików** przycisk opcji, podając ścieżkę systemu lokalnego.

 Po rozwiązania pomyślnie publikuje w programie SharePoint, rozwiązania pojawia się w **Galeria rozwiązań** możesz tu aktywować go. Aby uzyskać więcej informacji, zobacz [jak: Wdrażanie, publikowanie oraz aktualizowanie rozwiązań SharePoint na serwerze zdalnym](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

### <a name="upgrade-published-packages"></a>Uaktualnij pakiety opublikowane
 Jeśli wprowadzisz zmiany do projektu programu SharePoint w programie Visual Studio po opublikowaniu, opublikowany pakiet musi zostać uaktualniony, aby uwzględnić zmiany. Aby pomyślnie przeprowadzić uaktualnienie, pakiet musi mieć unikatową nazwę. Jeśli pakiet o tej samej nazwie znajduje się w witrynie programu SharePoint — które mogą wystąpić, gdy aktualizujesz istniejącą aplikację — alerty błędów nazwę pliku w konflikcie i umożliwia zmianę nazwy pakietu. Po ponowne opublikowanie, nowy pakiet pojawia się w witrynie programu SharePoint i mogą być uaktualniane. Uaktualnionego pakietu aktualizacji rozwiązania przy użyciu danych z pakietu starsze, a następnie aktywuje rozwiązanie w programie SharePoint. Aby uzyskać więcej informacji, zobacz [jak: Wdrażanie, publikowanie oraz aktualizowanie rozwiązań SharePoint na serwerze zdalnym](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

## <a name="see-also"></a>Zobacz także
- [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
