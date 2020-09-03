---
title: Konfiguracja projektu do kompilowania | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bdd084053e06206a99298b234b4d51c8504119a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706731"
---
# <a name="project-configuration-for-building"></a>Konfigurowanie projektu do kompilowania
Lista konfiguracji rozwiązań dla danego rozwiązania jest zarządzana przez okno dialogowe Konfiguracje rozwiązań.

 Użytkownik może tworzyć dodatkowe konfiguracje rozwiązań z własną unikatową nazwą. Gdy użytkownik tworzy nową konfigurację rozwiązania, IDE domyślnie odpowiada odpowiedniej nazwie konfiguracji w projektach lub Debuguj, jeśli nie istnieje odpowiednia nazwa. Użytkownik może zmienić zaznaczenie w razie potrzeby w celu spełnienia określonych wymagań. Jedyny wyjątek od tego zachowania polega na tym, że projekt obsługuje konfigurację zgodną z nazwą nowej konfiguracji rozwiązania. Załóżmy na przykład, że rozwiązanie zawiera Project1 i Project2. Project1 zawiera konfiguracje projektu Debug, detaliczne i MyConfig1. Project2 zawiera konfiguracje projektu Debug, detaliczne i MyConfig2.

 Jeśli użytkownik utworzy nową konfigurację rozwiązania o nazwie MyConfig2, Project1 domyślnie powiąże swoją konfigurację debugowania z konfiguracją rozwiązania. Program Project2 również domyślnie wiąże konfigurację MyConfig2 z konfiguracją rozwiązania.

> [!NOTE]
> W powiązaniu nie jest rozróżniana wielkość liter.

 Gdy użytkownik wybierze pozycję **wybór wielokrotny** na liście rozwijanej konfiguracja, środowisko wyświetli okno dialogowe z listą dostępnych konfiguracji.

 ![Wiele konfiguracji](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs") Wiele konfiguracji

 W tym oknie dialogowym użytkownik może wybrać jedną lub wiele konfiguracji. Po wybraniu wartości właściwości wyświetlane w oknie dialogowym strony właściwości odzwierciedlają przecięcie wartości dla wybranych konfiguracji.

 Aby uzyskać informacje dotyczące dodawania i zmieniania nazw konfiguracji dla rozwiązań i projektów, zobacz temat [Konfiguracja rozwiązania](../../extensibility/internals/solution-configuration.md) .

 Zależności projektu i kolejność kompilacji to konfiguracja rozwiązania niezależna: oznacza to, że można skonfigurować tylko jedno drzewo zależności dla wszystkich projektów w rozwiązaniu. Kliknięcie prawym przyciskiem myszy rozwiązania lub projektu i wybranie opcji **zależności projektu** lub **kolejność kompilacji projektu** powoduje otwarcie okna dialogowego **zależności projektu** . Można go również otworzyć z menu **projekt** .

 ![Zależności projektu](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies") Zależności projektu

 Zależności projektu określają kolejność, w której projekty są kompilowane. Karta kolejność kompilacji w oknie dialogowym umożliwia wyświetlenie dokładnej kolejności, w której zostaną skompilowane projekty w ramach rozwiązania, a następnie użyj karty zależności, aby zmodyfikować kolejność kompilacji.

> [!NOTE]
> Projekty na liście, które mają zaznaczone pola wyboru, ale są wygaszone, zostały dodane przez środowisko ze względu na jawne zależności określone przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interfejsy i nie można ich zmienić. Na przykład dodanie odwołania do projektu z [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projektu do innego projektu powoduje automatyczne dodanie zależności kompilacji, która może zostać usunięta tylko przez usunięcie odwołania. Projekty, których pola wyboru są wyczyszczone i są wyświetlane jako wygaszone, nie mogą być wybierane, ponieważ spowodowałoby to utworzenie pętli zależności (na przykład Project1 może być zależna od Project2, a Project2 będzie zależna od Project1), co mogłoby zawiesić kompilację.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] procesy kompilacji obejmują Typowe operacje kompilowania i łączenia, które są wywoływane za pomocą pojedynczego polecenia kompilacji. Obsługiwane są również dwa inne procesy kompilacji: czysta operacja usuwania wszystkich elementów wyjściowych z poprzedniej kompilacji oraz aktualna kontrola w celu ustalenia, czy element wyjściowy w konfiguracji został zmieniony.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> obiekty zwracają odpowiednie <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> (zwrócone z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A> ), aby zarządzać procesami kompilacji. Aby zgłosić stan operacji kompilacji w trakcie jej występowania, konfiguracje przeprowadzają wywołania do <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback> , interfejs zaimplementowany przez środowisko i inny obiekt, który interesuje kompilacje zdarzeń stanu.

 Po skompilowaniu ustawienia konfiguracji mogą służyć do określenia, czy mogą być uruchamiane w ramach kontroli debugera. Konfiguracje implementują <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> obsługę debugowania.

 Po wdrożeniu zależności projektu można programowo manipulować zależności za pomocą modelu automatyzacji. Wywołujesz <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> model automatyzacji. Nie ma dostępnych interfejsów poziomu API VSIP, które umożliwiają bezpośrednie manipulowanie konfiguracjami Menedżera kompilacji rozwiązań i ich właściwościami.

 Ponadto możesz udostępnić siatkę w oknie zależności projektu. Aby uzyskać więcej informacji, zobacz [właściwości wyświetlania siatki](../../extensibility/internals/properties-display-grid.md).

## <a name="see-also"></a>Zobacz też
- [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md)
- [Konfigurowanie projektu do zarządzania wdrożeniem](../../extensibility/internals/project-configuration-for-managing-deployment.md)
- [Konfigurowanie projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md)
