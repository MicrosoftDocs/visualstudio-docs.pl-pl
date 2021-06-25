---
title: Konfiguracja projektu na | Microsoft Docs
description: Dowiedz się, jak lista konfiguracji rozwiązań dla określonego rozwiązania jest zarządzana przez okno dialogowe Konfiguracje rozwiązań w nowym typie projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bf98698d3527220c4bc25cdf36132f0088ae4ea7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899930"
---
# <a name="project-configuration-for-building"></a>Konfigurowanie projektu do kompilowania
Lista konfiguracji rozwiązań dla danego rozwiązania jest zarządzana przez okno dialogowe Konfiguracje rozwiązań.

 Użytkownik może tworzyć dodatkowe konfiguracje rozwiązań, z których każda ma własną unikatową nazwę. Gdy użytkownik tworzy nową konfigurację rozwiązania, w środowiskach IDE jest domyślnie domyślną nazwą odpowiedniej konfiguracji w projektach lub Debuguj, jeśli nie istnieje żadna odpowiadająca nazwa. Użytkownik może zmienić wybór, aby w razie potrzeby spełniał określone wymagania. Jedynym wyjątkiem od tego zachowania jest sytuacja, gdy projekt obsługuje konfigurację, która jest taka sama jak nazwa nowej konfiguracji rozwiązania. Załóżmy na przykład, że rozwiązanie zawiera elementy Project1 i Project2. Projekt Project1 ma konfiguracje projektów Debug, Retail i MyConfig1. Projekt Project2 ma konfiguracje projektów Debug, Retail i MyConfig2.

 Jeśli użytkownik tworzy nową konfigurację rozwiązania o nazwie MyConfig2, projekt Project1 domyślnie wiąże konfigurację debugowania z konfiguracją rozwiązania. Projekt Project2 domyślnie wiąże również konfigurację myConfig2 z konfiguracją rozwiązania.

> [!NOTE]
> W powiązaniu nie jest uwzględniania litera.

 Gdy użytkownik wybierze **element** Wybór wielokrotny na liście rozwijanej konfiguracji, środowisko wyświetli okno dialogowe z listą dostępnych konfiguracji.

 ![Wiele konfiguracji](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs") Wiele konfiguracji

 W tym oknie dialogowym użytkownik może wybrać jedną lub wiele konfiguracji. Po wybraniu wartości właściwości wyświetlane na stronach właściwości w oknie dialogowym odzwierciedlają części wspólne wartości dla wybranych konfiguracji.

 Zobacz [Konfiguracja rozwiązania,](../../extensibility/internals/solution-configuration.md) aby uzyskać informacje dotyczące dodawania i zmieniania nazw konfiguracji dla rozwiązań i projektów.

 Zależności projektu i kolejność kompilacji są niezależne od konfiguracji rozwiązania: oznacza to, że można skonfigurować tylko jedno drzewo zależności dla wszystkich projektów w rozwiązaniu. Kliknięcie prawym przyciskiem myszy rozwiązania lub projektu i  wybranie opcji **Zależności** projektu lub Kolejność kompilacji projektu powoduje otwarcie okna **dialogowego** Zależności projektu. Można go również otworzyć z menu **Projekt.**

 ![Zależności projektu](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies") Zależności projektu

 Zależności projektu określają kolejność kompilowania projektów. Karta Kolejność kompilacji w oknie dialogowym umożliwia wyświetlenie dokładnej kolejności kompilowania projektów w ramach rozwiązania, a następnie użycie karty Zależności w celu zmodyfikowania kolejności kompilacji.

> [!NOTE]
> Projekty na liście, które mają zaznaczone pola wyboru, ale są wygaszone, zostały dodane przez środowisko z powodu jawnych zależności określonych przez interfejsy lub i nie można <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> ich zmienić. Na przykład dodanie odwołania do projektu z projektu do innego projektu powoduje automatyczne dodanie zależności kompilacji, która może zostać usunięta tylko [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] przez usunięcie odwołania. Nie można wybrać projektów, których pola wyboru są jasne i są wyświetlane jako wygaszone, ponieważ w ten sposób utworzy się pętla zależności (na przykład projekt Project1 będzie zależny od project2, a projekt Project2 będzie zależny od project1), co wsadowałoby kompilację.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Procesy kompilacji obejmują typowe operacje kompilacji i łączenia wywoływane za pomocą jednego polecenia kompilacji. Obsługiwane mogą być również dwa inne procesy kompilacji: czysta operacja usuwania wszystkich elementów wyjściowych z poprzedniej kompilacji oraz aktualne sprawdzanie w celu określenia, czy element wyjściowy w konfiguracji uległ zmianie.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> Obiekty zwracają odpowiedni <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> (zwrócony z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A> ) do zarządzania procesami kompilacji. Aby zgłosić stan operacji kompilacji podczas jej wystąpienia, konfiguracje wywołuje , interfejs zaimplementowany przez środowisko i dowolny inny obiekt zainteresowany <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback> zdarzeniami stanu kompilacji.

 Po s zbudowaniu ustawień konfiguracji można określić, czy można je uruchamiać pod kontrolą debugera. Konfiguracje <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> implementują obsługę debugowania.

 Po zaimplementowaniu zależności projektu można programowo manipulować zależnościami za pomocą modelu automatyzacji. Wywołanie jest <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> w modelu automatyzacji. Nie ma dostępnych interfejsów API programu VSIP, które umożliwiają bezpośrednie manipulowanie konfiguracjami menedżera kompilacji rozwiązań i ich właściwościami.

 Ponadto można udostępnić siatkę w oknie zależności projektu. Aby uzyskać więcej informacji, zobacz [Properties Display Grid (Siatka wyświetlana właściwości).](../../extensibility/internals/properties-display-grid.md)

## <a name="see-also"></a>Zobacz też
- [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md)
- [Konfigurowanie projektu do zarządzania wdrożeniem](../../extensibility/internals/project-configuration-for-managing-deployment.md)
- [Konfigurowanie projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md)
