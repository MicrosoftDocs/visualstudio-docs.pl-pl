---
title: 'Jak: Otwórz edytory otwartych dokumentów | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03d0986573ac0d53427f6490370be2bfa1c4cbe7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710918"
---
# <a name="how-to-open-editors-for-open-documents"></a>Jak: Otwieranie edytorów otwartych dokumentów
Zanim projekt otworzy okno dokumentu, projekt musi najpierw określić, czy plik jest już otwarty w oknie dokumentu dla innego edytora. Plik może być otwarty w edytorze specyficznym dla projektu lub [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]jeden ze standardowych edytorów zarejestrowanych w programie .

## <a name="open-a-project-specific-editor"></a>Otwieranie edytora specyficznego dla projektu
 Poniższa procedura służy do otwierania edytora specyficznego dla projektu dla pliku, który jest już otwarty.

### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Aby otworzyć edytor specyficzny dla projektu dla otwartego pliku

1. Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> metody.

    To wywołanie zwraca wskaźniki do hierarchii dokumentu, elementu hierarchii i ramki okna, jeśli to konieczne.

2. Jeśli dokument jest otwarty, projekt musi sprawdzić, czy istnieje tylko obiekt danych dokumentu lub czy obiekt widoku dokumentu jest również obecny.

   - Jeśli obiekt widoku dokumentu istnieje, a ten widok jest dla innej hierarchii lub elementu hierarchii, projekt używa wskaźnika do ramki okna widoku, aby ponownie wyświetlić istniejące okno.

   - Jeśli obiekt widoku dokumentu istnieje, a ten widok jest dla tej samej hierarchii i elementu hierarchii, projekt może otworzyć drugi widok, jeśli można dołączyć do obiektu danych dokumentu źródłowego. W przeciwnym razie projekt należy użyć wskaźnika do ramki okna widoku, aby ponownie wyświetlić istniejące okno.

   - Jeśli istnieje tylko obiekt danych dokumentu, projekt powinien określić, czy może używać obiektu danych dokumentu dla swojego widoku. Jeśli obiekt danych dokumentu jest zgodny, wykonaj czynności opisane w [artykule Otwórz edytor specyficzny dla projektu](../extensibility/how-to-open-project-specific-editors.md).

     Jeśli obiekt danych dokumentu nie jest zgodny, użytkownik powinien zostać wyświetlony błąd wskazujący, że plik jest obecnie używany. Ten błąd powinien być wyświetlany tylko w przypadkach przejściowych, takich jak podczas kompilowania pliku w tym samym czasie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] użytkownik próbuje otworzyć plik przy użyciu edytora innego niż podstawowy edytor tekstu. Podstawowy edytor tekstu może udostępniać obiekt danych dokumentu z kompilatorem.

3. Jeśli dokument nie jest otwarty, ponieważ nie ma obiektu danych dokumentu ani obiektu widoku dokumentu, wykonaj kroki opisane w polu [Otwórz edytor specyficzny dla projektu](../extensibility/how-to-open-project-specific-editors.md).

## <a name="open-a-standard-editor"></a>Otwieranie standardowego edytora
 Poniższa procedura służy do otwierania standardowego edytora pliku, który jest już otwarty.

### <a name="to-open-a-standard-editor-for-an-open-file"></a>Aby otworzyć standardowy edytor otwartego pliku

1. Zadzwoń <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.

     Ta metoda najpierw sprawdza, czy dokument nie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>jest jeszcze otwarty przez wywołanie . Jeśli dokument jest już otwarty, jego okno edytora zostanie ponownie odsłonięte.

2. Jeśli dokument nie jest otwarty, wykonaj czynności opisane w [trybie : Otwórz edytory standardowe](../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Zobacz też
- [Otwieranie i zapisywanie elementów projektu](../extensibility/internals/opening-and-saving-project-items.md)
- [Jak: Otwieranie edytorów specyficznych dla projektu](../extensibility/how-to-open-project-specific-editors.md)
- [Jak: Otwórz edytory standardowe](../extensibility/how-to-open-standard-editors.md)
