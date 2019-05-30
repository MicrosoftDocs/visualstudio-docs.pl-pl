---
title: Rozszerzanie i dostosowywanie narzędzi Windows | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c0eafb5a95151d6c3a805ad4d51c847f2fbe269d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341144"
---
# <a name="extend-and-customize-tool-windows"></a>Rozszerzanie i dostosowywanie okien narzędzi
Visual Studio zawiera kilka różnych typów windows, na przykład okien, okien dokumentu i okno dialogowe systemu windows. Inne okna, takie jak **właściwości** oknie **dane wyjściowe** oknie i **listy zadań** oknie rodzaje okien narzędzi.

## <a name="tool-windows"></a>Okna narzędzi
 Okna narzędzi w usłudze Visual Studio są zwykle tylko do odczytu systemu windows, które nie są oparte na plikach. W tym będą się różnić od okna dokumentów, które zawierają pliki w trybie odczytu i zapisu. **Przybornika**, **Eksploratora rozwiązań**, **właściwości** oknie i **przeglądarki sieci Web** to przykłady okien narzędzi.

 Aby dowiedzieć się, jak utworzyć okno prostego narzędzia, zobacz [Dodawanie okna narzędzi](../extensibility/adding-a-tool-window.md).

 Aby zarejestrować okna narzędzi programu Visual Studio, zobacz [rejestrowanie okna narzędzi](../extensibility/registering-a-tool-window.md).

 Okna narzędzi są jednym wystąpieniu domyślnie, co oznacza, że tylko jedno wystąpienie okna narzędzia może być otwarty naraz. Po otwarciu okna narzędzi jednego wystąpienia zostanie zamknięte przed zamknięciem IDE. Po zamknięciu okna narzędzi jednego wystąpienia zmienia tylko jego widoczność. Można również utworzyć wiele wystąpień narzędzia windows tak, aby wiele wystąpień okna może być otwarty jednocześnie. Zobacz [utworzenie okna narzędzia obejmujące wiele wystąpień](../extensibility/creating-a-multi-instance-tool-window.md) Aby uzyskać więcej informacji.

 Okna narzędzi mogą być *dynamiczne*, co oznacza, że są one widoczne zawsze wtedy, gdy dotyczą ich powiązane kontekstu interfejsu użytkownika. Korzystanie z automatycznego widoczność można zaśmiecać okna w IDE. Aby uzyskać więcej informacji, zobacz [Otwieranie dynamicznego okna narzędzi](../extensibility/opening-a-dynamic-tool-window.md).

 Okna narzędzi może być zadokowane, zmiennoprzecinkowego lub z kartami w ramce dokumentu. Ramka okna narzędzia są dostarczane przez środowisko IDE i jest używane do kontrolowania rozmiaru, lokalizacji, stan dokowania i inne właściwości trwałe. Zawartość jest wyświetlana w okienku okna narzędzia. Domyślnym rozmiarem i lokalizacją zastosować, tylko gdy okno narzędzia pierwszym otwarciu; Po utworzeniu tego stanu okna Narzędzie jest trwały.

 Narzędzie okienka mogą hostowanie kontrolki użytkownika WPF i obsługiwać pasków narzędzi. Można zastąpić <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> właściwość zwraca uchwyt obsługiwanego formantu.

 Możesz dodać wiele różnych funkcji do okna narzędzi. Na przykład można dodać paska narzędzi: [Dodawanie paska narzędzi do okna narzędzi](../extensibility/adding-a-toolbar-to-a-tool-window.md) lub menu skrótów: [Dodawanie menu skrótów w oknie narzędzia](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Można dodać kontrolkę wyszukiwania, która umożliwia wyszukiwanie elementów wewnątrz okna narzędzia: [Dodawanie wyszukiwania do okna narzędzi](../extensibility/adding-search-to-a-tool-window.md).

 Można subskrybować zdarzenia okna narzędzia: [Subskrybowanie zdarzenia](../extensibility/subscribing-to-an-event.md).

## <a name="extend-existing-tool-windows"></a>Rozszerzanie istniejących narzędzi systemu windows
 Można dodać informacji o okna narzędzia do nowego **opcje** strony i nowe ustawienie na **właściwości** strony, zapisać **listy zadań** i **danych wyjściowych**  systemu windows. Aby uzyskać więcej informacji, zobacz [rozszerzyć okna właściwości, listy zadań, danych wyjściowych i opcji](../extensibility/extending-the-properties-task-list-output-and-options-windows.md) i [rozszerzyć okna właściwości, listy zadań, danych wyjściowych i opcji](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).

## <a name="modal-dialog-boxes"></a>Modalne okna dialogowe
 W rozszerzeniu Visual Studio, należy utworzyć modalnych okien dialogowych za pochodząca od <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>, co pozwala na kontrolowanie ich i pozostałych interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [tworzenie i zarządzanie modalne okna dialogowe](../extensibility/creating-and-managing-modal-dialog-boxes.md).

## <a name="see-also"></a>Zobacz także
- [Tworzenie rozszerzenia za pomocą okna narzędzi](../extensibility/creating-an-extension-with-a-tool-window.md)