---
title: Rozszerzanie i dostosowywanie narzędzi Windows | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b232fa1275bce453e3b32cea6a5ff37fdd501c6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204540"
---
# <a name="extending-and-customizing-tool-windows"></a>Rozszerzanie i dostosowywanie okien narzędzi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio zawiera kilka różnych typów windows, na przykład okien, okien dokumentu i okno dialogowe systemu windows. Inne okna, takie jak okno właściwości, w oknie danych wyjściowych i oknie Lista zadań są typy okien narzędzi.  
  
## <a name="tool-windows"></a>Narzędzie Windows  
 Okna narzędzi w usłudze Visual Studio są zwykle tylko do odczytu systemu windows, które nie są oparte na plikach. W tym będą się różnić od okna dokumentów, które zawierają pliki w trybie odczytu i zapisu. **Przybornika**, **Eksploratora rozwiązań**, **właściwości** oknie i **przeglądarki sieci Web** to przykłady okien narzędzi.  
  
 Aby dowiedzieć się, jak utworzyć okno prostego narzędzia, zobacz [Dodawanie okna narzędzi](../extensibility/adding-a-tool-window.md).  
  
 Aby zarejestrować okna narzędzi programu Visual Studio, zobacz [rejestrowanie okna narzędzi](../extensibility/registering-a-tool-window.md).  
  
 Okna narzędzi są jednym wystąpieniu domyślnie, co oznacza, że tylko jedno wystąpienie okna narzędzia może być otwarty naraz. Po otwarciu okna narzędzi jednego wystąpienia zostanie zamknięte przed zamknięciem IDE. Po zamknięciu okna narzędzi jednego wystąpienia zmienia tylko jego widoczność. Można również utworzyć wiele wystąpień narzędzia windows tak, aby wiele wystąpień okna może być otwarty jednocześnie. Zobacz [tworzenia okna narzędzia obejmujące wiele wystąpień](../extensibility/creating-a-multi-instance-tool-window.md) Aby uzyskać więcej informacji.  
  
 Okna narzędzi mogą być *dynamiczne*, co oznacza, że są one widoczne zawsze wtedy, gdy dotyczą ich powiązane kontekstu interfejsu użytkownika. Korzystanie z automatycznego widoczność można zaśmiecać okna w IDE. Aby uzyskać więcej informacji, zobacz [Otwieranie dynamicznego okna narzędzi](../extensibility/opening-a-dynamic-tool-window.md).  
  
 Okna narzędzi może być zadokowane, zmiennoprzecinkowego lub z kartami w ramce dokumentu. Ramka okna narzędzia są dostarczane przez środowisko IDE i jest używane do kontrolowania rozmiaru, lokalizacji, stan dokowania i inne właściwości trwałe. Zawartość jest wyświetlana w okienku okna narzędzia. Domyślnym rozmiarem i lokalizacją zastosować, tylko gdy okno narzędzia pierwszym otwarciu; Po utworzeniu tego stanu okna Narzędzie jest trwały.  
  
 Narzędzie okienka mogą hostowanie kontrolki użytkownika WPF i obsługiwać pasków narzędzi. Można zastąpić <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> właściwość zwraca uchwyt obsługiwanego formantu.  
  
 Możesz dodać wiele różnych funkcji do okna narzędzi. Na przykład można dodać paska narzędzi: [Dodawanie paska narzędzi do okna narzędzi](../extensibility/adding-a-toolbar-to-a-tool-window.md) lub menu skrótów: [Dodawanie Menu skrótów w oknie narzędzia](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Można dodać kontrolkę wyszukiwania, która umożliwia wyszukiwanie elementów wewnątrz okna narzędzia: [Dodawanie wyszukiwania do okna narzędzi](../extensibility/adding-search-to-a-tool-window.md).  
  
 Można subskrybować zdarzenia okna narzędzia: [Subskrybowanie zdarzenia](../extensibility/subscribing-to-an-event.md).  
  
## <a name="extending-existing-tool-windows"></a>Rozszerzanie istniejących narzędzi Windows  
 Można dodać informacji o okna narzędzia do nowego **opcje** strony i nowe ustawienie na **właściwości** strony, zapisać **listy zadań** i **danych wyjściowych**  systemu windows. Aby uzyskać więcej informacji, zobacz [rozszerzanie właściwości, listy zadań, danych wyjściowych i opcji Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md) i [rozszerzanie właściwości, listy zadań, danych wyjściowych i opcji Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).  
  
## <a name="modal-dialog-boxes"></a>Modalne okna dialogowe  
 W rozszerzeniu Visual Studio, należy utworzyć modalnych okien dialogowych za pochodząca od <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>, co pozwala na kontrolowanie ich i pozostałych interfejsu użytkownika. Aby uzyskać więcej informacji zobacz. [Tworzenie i zarządzanie modalne okna dialogowe](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie rozszerzenia za pomocą okna narzędzi](../extensibility/creating-an-extension-with-a-tool-window.md)
