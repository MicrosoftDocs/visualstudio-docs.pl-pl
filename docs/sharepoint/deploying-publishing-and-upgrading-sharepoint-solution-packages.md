---
title: Wdrażanie, publikowanie, & uaktualnianie pakietów rozwiązania SharePoint
description: Wdrażaj, Publikuj i uaktualniaj pakiety rozwiązań programu SharePoint. Dostosuj proces wdrażania. Publikowanie pakietów na serwerze zdalnym lub lokalnym.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cd0dfa3a12c675463c46e93aa0d5b25e8b4bd4b2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948859"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>Wdrażanie, publikowanie i uaktualnianie pakietów rozwiązania SharePoint
  Po opracowaniu rozwiązania SharePoint w programie Visual Studio można wdrożyć jego plik pakietu (wsp) na lokalnym serwerze programu SharePoint lub opublikować go na zdalnym lub lokalnym serwerze programu SharePoint. W przypadku wdrażania plików można dostosować sposób wdrażania plików pakietu (wsp).

> [!NOTE]
> Obecnie tylko rozwiązania w trybie piaskownicy mogą być publikowane na zdalnych serwerach programu SharePoint. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące rozwiązania w trybie piaskownicy](../sharepoint/sandboxed-solution-considerations.md).

## <a name="deploy-publish-and-upgrade"></a>Wdrażanie, publikowanie i uaktualnianie
 *Wdrożenie* odwołuje się do kopiowania pliku rozwiązania programu SharePoint skompilowanego z projektu programu SharePoint w programie Visual Studio do hosta lokalnego. W wdrożonym rozwiązaniu można skonfigurować kroki wdrażania, takie jak odtwarzanie puli Internet Information Services (IIS), aktywowanie rozwiązania po wdrożeniu itd. W celu wdrożenia programu Użyj polecenia **Wdróż** w menu **kompilacja** . Aby uzyskać więcej informacji, zobacz [jak: edytowanie konfiguracji wdrożenia programu SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) i [instrukcje: wdrażanie i publikowanie rozwiązania SharePoint w lokalnej witrynie programu SharePoint](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 *Publikowanie* odwołuje się do przekazywania pliku rozwiązania SharePoint w trybie piaskownicy do zdalnej witryny programu SharePoint; oznacza to, że lokacja znajduje się w innym systemie. Możesz również opublikować plik rozwiązania w trybie piaskownicy programu SharePoint w lokalnej witrynie programu SharePoint, ale bez względu na to, czy lokacja opublikowana jako lokalna, czy zdalna, nie można skonfigurować jej kroków wdrożenia.

 *Uaktualnianie* dotyczy aktualizacji istniejącego zdalnego lub lokalnie opublikowanego rozwiązania programu SharePoint. Po wprowadzeniu jakichkolwiek zmian w rozwiązaniu programu SharePoint w programie Visual Studio należy zmienić nazwę pliku pakietu rozwiązania, opublikować ponownie rozwiązanie, a następnie uaktualnić rozwiązanie po jego pomyślnym ponownym opublikowaniu. Po ponownym opublikowaniu rozwiązania opublikowanego lokalnie można zastąpić istniejący plik rozwiązania.

## <a name="deploy-packages"></a>Wdróż pakiety
 Pliki pakietu można wdrożyć na serwerze programu SharePoint na komputerze deweloperskim w celu testowania i debugowania. Można również utworzyć plik pakietu, który można zainstalować na innym komputerze, wybierając przycisk opcji **Publikuj w systemie plików** w oknie dialogowym **Publikowanie** . Pakiet jest tworzony i kopiowany do określonej ścieżki pliku lokalnego. Aby wdrożyć rozwiązanie programu SharePoint na serwerze lokalnym, użyj polecenia **Wdróż** w menu **kompilacja** . Aby uzyskać więcej informacji, zobacz [jak: wdrażanie i publikowanie rozwiązania SharePoint w lokalnej witrynie programu SharePoint](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).

 Aby dowiedzieć się, jak wdrożyć definicję listy, dodać odbiorcę zdarzeń i korzystać z projektanta funkcji i projektanta pakietów, zobacz [Przewodnik: wdrażanie definicji listy zadań projektu](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md).

## <a name="customize-the-deployment-process"></a>Dostosowywanie procesu wdrażania
 W poniższej tabeli przedstawiono dwie konfiguracje wdrażania, których można użyć podczas debugowania i wdrażania rozwiązania programu SharePoint.

|Konfiguracja wdrożenia|Opis|
|------------------------------|-----------------|
|Domyślne|Domyślna konfiguracja wdrożenia. Wykonywane są następujące kroki wdrażania:<br /><br /> 1. Uruchom polecenie przed wdrożeniem.<br />2. Odtwórz pulę aplikacji usług IIS.<br />3. wycofywanie rozwiązania.<br />4. Dodaj rozwiązanie.<br />5. Aktywuj funkcje.<br />6. Uruchom polecenie po wdrożeniu.<br /><br /> Po odinstalowaniu pakietu są wykonywane następujące czynności wycofywania.<br /><br /> 1. Odtwórz pulę aplikacji usług IIS.<br />2. wycofywanie rozwiązania.|
|Brak aktywacji|Ta konfiguracja wdrożenia uruchamia te same kroki jak konfiguracja domyślna, ale pomija krok aktywacji.|

 Możesz utworzyć własne konfiguracje wdrożenia, aby ukończyć pojedynczy krok lub zmienić kolejność kroków w procesie wdrażania. Aby uzyskać więcej informacji, zobacz [How to: Edit a SharePoint Deployment Configuration](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).

 Możesz również dodać polecenia do uruchomienia przed i po wdrożeniu. Aby uzyskać więcej informacji, zobacz [How to: Set SharePoint Deployment Commands](../sharepoint/how-to-set-sharepoint-deployment-commands.md).

## <a name="publish-packages-to-a-remote-or-local-server"></a>Publikowanie pakietów na serwerze zdalnym lub lokalnym
 Aby opublikować rozwiązanie programu SharePoint w trybie piaskownicy na serwerze zdalnym, na pasku menu wybierz **kompilację**, **Opublikuj**, a następnie w oknie dialogowym **Publikowanie** wybierz przycisk opcji **Publikuj w witrynie programu SharePoint** , podając adres URL serwera zdalnego, na przykład `https://someremoteserver.sharepoint.microsoftonline.com` .

 Aby opublikować rozwiązanie SharePoint na serwerze lokalnym, w oknie dialogowym **Publikowanie** wybierz przycisk opcji **Publikuj w systemie plików** , podając ścieżkę systemu lokalnego.

 Po pomyślnym opublikowaniu rozwiązania w programie SharePoint rozwiązanie pojawi się w **galerii rozwiązań** , w którym można ją aktywować. Aby uzyskać więcej informacji, zobacz [jak: wdrażanie, publikowanie i uaktualnianie rozwiązań SharePoint na serwerze zdalnym](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

### <a name="upgrade-published-packages"></a>Uaktualnianie opublikowanych pakietów
 Jeśli wprowadzisz jakiekolwiek zmiany w projekcie programu SharePoint w programie Visual Studio po jego opublikowaniu, należy uaktualnić opublikowany pakiet, aby uwzględnić zmiany. Aby uaktualnienie powiodło się, pakiet musi mieć unikatową nazwę. Jeśli w witrynie programu SharePoint zostanie znaleziony pakiet o tej samej nazwie, który może wystąpić w przypadku aktualizowania istniejącej aplikacji — błąd powoduje wyświetlenie alertu dotyczącego konfliktu nazw plików i pozwala zmienić nazwę pakietu. Po ponownym opublikowaniu nowy pakiet zostanie wyświetlony w witrynie programu SharePoint i będzie można go uaktualnić. Uaktualniony pakiet aktualizuje rozwiązanie przy użyciu danych ze starszego pakietu, a następnie aktywuje rozwiązanie w programie SharePoint. Aby uzyskać więcej informacji, zobacz [jak: wdrażanie, publikowanie i uaktualnianie rozwiązań SharePoint na serwerze zdalnym](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).

## <a name="see-also"></a>Zobacz też
- [Pakowanie i wdrażanie rozwiązań SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
