---
title: Konfiguracja do kompilowania projektu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], configuration for building
- project configurations, building
ms.assetid: 2c83615d-fa4d-4b9f-b315-7a69b3000da0
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 953a02c27f40e92c41d2e43bc818727118eb0a27
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434847"
---
# <a name="project-configuration-for-building"></a>Konfigurowanie projektu do kompilowania
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Lista konfiguracje rozwiązania dla danego rozwiązania jest zarządzany przez okna dialogowego konfiguracje rozwiązania.  
  
 Użytkownik może utworzyć rozwiązanie dodatkowe konfiguracje, każdy z własną unikatową nazwę. Gdy użytkownik tworzy nową konfigurację rozwiązania, IDE domyślnie nazwę konfiguracji w projektach, lub debugowania, jeśli nie ma żadnej odpowiednie nazwy. Użytkownik może zmienić wybór, aby spełniały określone wymagania, jeśli to konieczne. Jedyny wyjątek od to zachowanie jest, gdy projekt obsługuje konfigurację, która jest zgodna z nazwą nowa konfiguracja rozwiązania. Załóżmy na przykład, że rozwiązanie zawiera projektu Project1 i o nazwie Project2. Projektu Project1 ma konfiguracje projektu debugowania, handel detaliczny i MyConfig1. O nazwie Project2 ma konfiguracje projektu debugowania, handel detaliczny i MyConfig2.  
  
 Jeśli użytkownik tworzy nowa konfiguracja rozwiązania o nazwie MyConfig2, projektu Project1 wiąże swoją konfigurację debugowania konfiguracji rozwiązania domyślnie. O nazwie Project2 także wiąże jego konfigurację MyConfig2 konfiguracji rozwiązania domyślnie.  
  
> [!NOTE]
> Powiązanie jest rozróżniana wielkość liter.  
  
 Gdy użytkownik wybierze **wybór wielokrotny** elementu na liście rozwijanej Konfiguracja środowiska wyświetlane jest okno dialogowe, które zawiera listę dostępnych konfiguracji.  
  
 ![Wiele konfiguracji](../../extensibility/internals/media/vsmultiplecfgs.gif "vsMultipleCfgs")  
Wiele konfiguracji  
  
 W oknie dialogowym użytkownik może wybrać jednego lub wielu konfiguracji. Po wybraniu wartości właściwości wyświetlane w oknie dialogowym stron właściwości odzwierciedlają część wspólną wartości dla wybranej konfiguracji.  
  
 Zobacz [konfiguracji rozwiązania](../../extensibility/internals/solution-configuration.md) informacji dotyczących dodawania i zmiana nazwy konfiguracji dla rozwiązań i projektów.  
  
 Zależności projektu i kolejność kompilacji są niezależne konfiguracji rozwiązania: oznacza to, należy skonfigurować tylko jedną zależność drzewa dla wszystkich projektów w rozwiązaniu. Kliknij prawym przyciskiem myszy rozwiązanie lub projekt, a następnie wybierając opcję **zależności projektu** lub **kolejność kompilacji projektu** opcję otwarcia **zależności projektu** okno dialogowe. Można go również otworzyć z **projektu** menu.  
  
 ![Project Dependencies](../../extensibility/internals/media/vsprojdependencies.gif "vsProjDependencies")  
Zależności projektu  
  
 Zależności projektu określają kolejność, w którym projekty są kompilowane. Karta kolejność kompilacji w oknie dialogowym dokładnie kolejność, w którym projektów w rozwiązaniu zostaną kompilacji i użyj karty zależności Aby zmodyfikować kolejność kompilacji.  
  
> [!NOTE]
> Projekty na liście, ich wybrane pola wyboru, które są wyszarzone, zostały dodane przez środowisko z powodu jawne zależności, określony przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildDependency> lub <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployDependency> interfejsy i nie można zmienić. Na przykład dodanie odwołania do projektu z [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] projektu do innego projektu automatycznie dodaje zależność kompilacji, które mogą zostać usunięte tylko przez usunięcie odwołania. Nie można wybrać projekty, których pola wyboru są wyraźne, a są wyszarzone, ponieważ to spowodowałoby utworzenie pętli zależności (na przykład projektu Project1 są zależne od Project2 i o nazwie Project2 są zależne od projektu Project1), który będzie zatrzymania kompilacji.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] procesy kompilacji obejmują typowe kompilacji i operacje łącze, które są wywoływane przy użyciu jednego polecenia kompilacji. Dwa procesy kompilacji mogą być również obsługiwane: operacji czyszczenia, aby usunąć wszystkie elementy wyjściowe z poprzedniej kompilacji i Sprawdzanie aktualności, aby ustalić, czy element danych wyjściowych w konfiguracji został zmieniony.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> Obiekt zwraca odpowiedni <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> (zwrócone w wyniku <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>) do zarządzania ich procesy kompilacji. Aby zgłosić stan operacji tworzenia, sprawdzeniem, konfiguracje wykonywać wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildStatusCallback>interfejs implementowany przez środowisko i inne obiekty są Państwo zainteresowani zdarzeń Stan kompilacji.  
  
 Po skompilowaniu ustawienia konfiguracji może służyć do określenia, czy zadania mogą być uruchamiane pod kontrolą debugera. Konfiguracje wdrożenia <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg> do obsługi debugowania.  
  
 Po zaimplementowaniu zależności projektu, można programowo manipulować zależności za pomocą modelu automatyzacji. Należy wywołać <xref:EnvDTE.SolutionBuild.BuildDependencies%2A> w modelu automatyzacji. Nie ma żadnych dostępnych interfejsów poziom interfejsu API VSIP, zezwalających na bezpośrednią manipulację konfiguracje Menedżera kompilacji rozwiązania i ich właściwości.  
  
 Ponadto możesz podać siatki w oknie zależności projektu. Aby uzyskać więcej informacji, zobacz [siatka wyświetlania właściwości](../../extensibility/internals/properties-display-grid.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie opcjami konfiguracji](../../extensibility/internals/managing-configuration-options.md)   
 [Konfigurowanie projektu do zarządzania wdrożeniem](../../extensibility/internals/project-configuration-for-managing-deployment.md)   
 [Konfigurowanie projektu dla danych wyjściowych](../../extensibility/internals/project-configuration-for-output.md)
