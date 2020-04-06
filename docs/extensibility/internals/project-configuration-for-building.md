---
title: Konfiguracja projektu dla budynku | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706731"
---
# <a name="project-configuration-for-building"></a>Konfigurowanie projektu do kompilowania
Lista konfiguracji rozwiązania dla danego rozwiązania jest zarządzana przez okno dialogowe Konfiguracje rozwiązania.

 Użytkownik może tworzyć dodatkowe konfiguracje rozwiązania, z których każda ma własną unikatową nazwę. Gdy użytkownik tworzy nową konfigurację rozwiązania, IDE domyślnie odpowiedniej nazwy konfiguracji w projektach lub debugowania, jeśli nie istnieje odpowiednia nazwa. Użytkownik może zmienić wybór, aby spełnić określone wymagania, jeśli to konieczne. Jedynym wyjątkiem od tego zachowania jest, gdy projekt obsługuje konfigurację, która pasuje do nazwy nowej konfiguracji rozwiązania. Załóżmy na przykład, że rozwiązanie zawiera Project1 i Project2. Project1 ma konfiguracje projektu Debug, Retail i MyConfig1. Project2 ma konfiguracje projektu Debug, Retail i MyConfig2.

 Jeśli użytkownik utworzy nową konfigurację rozwiązania o nazwie MyConfig2, Project1 domyślnie wiąże jego konfigurację debugowania z konfiguracją rozwiązania. Project2 wiąże również jego konfiguracji MyConfig2 do konfiguracji rozwiązania domyślnie.

> [!NOTE]
> Powiązanie jest niewrażliwe na przypadek.

 Gdy użytkownik wybierze element **wielokrotnego zaznaczenia** na liście rozwijanej konfiguracji, środowisko wyświetla okno dialogowe, które zawiera listę dostępnych konfiguracji.

 ![Wiele konfiguracji](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs") Wiele konfiguracji

 W tym oknie dialogowym użytkownik może wybrać jedną lub wiele konfiguracji. Po wybraniu wartości właściwości wyświetlane w oknie dialogowym strony właściwości odzwierciedlają przecięcie wartości dla wybranych konfiguracji.

 Zobacz [Konfiguracja rozwiązania,](../../extensibility/internals/solution-configuration.md) aby uzyskać informacje dotyczące dodawania i zmieniania nazw konfiguracji rozwiązań i projektów.

 Zależności projektu i kolejność kompilacji są niezależne od konfiguracji rozwiązania: oznacza to, że można skonfigurować tylko jedno drzewo zależności dla wszystkich projektów w rozwiązaniu. Kliknięcie prawym przyciskiem myszy rozwiązania lub projektu i wybranie opcji Zależności projektu lub Kolejność **kompilacji** **projektu** powoduje otwarcie okna dialogowego **Zależności projektu.** Można go również otworzyć z menu **Projekt.**

 ![Zależności projektu](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies") Zależności projektu

 Zależności projektu określają kolejność, w jakiej kompilacji projektów. Użyj karty Kolejność kompilacji w oknie dialogowym, aby wyświetlić dokładną kolejność tworzenia projektów w ramach rozwiązania, a następnie użyć karty Zależności, aby zmodyfikować kolejność kompilacji.

> [!NOTE]
> Projekty na liście, które mają zaznaczone pola wyboru, ale pojawiają się wygaszone <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> zostały <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> dodane przez środowisko z powodu jawnych zależności określonych przez interfejsy lub i nie można ich zmienić. Na przykład dodanie odwołania do [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] projektu z projektu do innego projektu automatycznie dodaje zależność kompilacji, którą można usunąć tylko przez usunięcie odwołania. Projekty, których pola wyboru są jasne i pojawiają się wygaszone nie można wybrać, ponieważ w ten sposób utworzy pętlę zależności (na przykład Project1 będzie zależny od projektu2, a Project2 będzie zależny od projektu Project1), co spowoduje wstrzymanie kompilacji.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]procesy kompilacji obejmują typowe operacje kompilacji i łącza, które są wywoływane za pomocą jednego polecenia Kompilacja. Dwa inne procesy kompilacji mogą być również obsługiwane: czysta operacja, aby usunąć wszystkie elementy wyjściowe z poprzedniej kompilacji i aktualne sprawdzenie, aby ustalić, czy element wyjściowy w konfiguracji uległ zmianie.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>obiekty zwracają <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> odpowiednie (zwrócone z <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>) do zarządzania ich procesów kompilacji. Aby zgłosić stan operacji kompilacji, podczas gdy występuje, <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>konfiguracje wywołać , interfejs zaimplementowany przez środowisko i inny obiekt zainteresowany zdarzenia stanu kompilacji.

 Po zbudowaniu ustawienia konfiguracji mogą służyć do określenia, czy mogą być uruchamiane pod kontrolą debugera. Konfiguracje <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> implementują do obsługi debugowania.

 Po zaimplementowanie zależności projektu, można programowo manipulować zależności za pośrednictwem modelu automatyzacji. Wywołanie <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> w modelu automatyzacji. Nie ma dostępnych interfejsów na poziomie interfejsu API VSIP, które umożliwiają bezpośrednią manipulację konfiguracjami menedżera kompilacji rozwiązania i ich właściwości.

 Ponadto można podać siatkę w oknie zależności projektu. Aby uzyskać więcej informacji, zobacz [Właściwości siatki wyświetlania](../../extensibility/internals/properties-display-grid.md).

## <a name="see-also"></a>Zobacz też
- [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md)
- [Konfigurowanie projektu do zarządzania wdrożeniem](../../extensibility/internals/project-configuration-for-managing-deployment.md)
- [Konfigurowanie projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md)
