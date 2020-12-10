---
title: 'Instrukcje: otwieranie edytorów dla otwartych dokumentów | Microsoft Docs'
description: Dowiedz się, jak otworzyć plik w standardowym lub specyficznym dla projektu edytorze. Gdy projekt otwiera okno dokumentu, musi określić, czy plik jest już otwarty.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d329ce7b4f4b74b8ff77357393ffe9383a3977e
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993864"
---
# <a name="how-to-open-editors-for-open-documents"></a>Instrukcje: otwieranie edytorów dla otwartych dokumentów
Przed otwarciem okna dokumentu przez projekt najpierw należy określić, czy plik jest już otwarty w oknie dokumentu dla innego edytora. Plik może być otwarty w edytorze specyficznym dla projektu lub jednym z edytorów standardowych zarejestrowanych w programie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="open-a-project-specific-editor"></a>Otwórz Edytor specyficzny dla projektu
 Aby otworzyć Edytor specyficzny dla projektu dla pliku, który jest już otwarty, należy wykonać czynności opisane w poniższej procedurze.

### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Aby otworzyć Edytor specyficzny dla projektu dla otwartego pliku

1. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> metodę.

    To wywołanie zwraca wskaźniki do hierarchii dokumentu, elementu hierarchii i ramki okna, jeśli jest to konieczne.

2. Jeśli dokument jest otwarty, projekt musi sprawdzić, czy tylko obiekt danych dokumentu istnieje, czy też w przypadku obecnego obiektu widoku dokumentu.

   - Jeśli obiekt widoku dokumentu istnieje, a ten widok jest dla innej hierarchii lub elementu hierarchii, projekt używa wskaźnika do ramki okna widoku, aby zmienić powierzchnię istniejącego okna.

   - Jeśli obiekt widoku dokumentu istnieje i ten widok jest przeznaczony dla tej samej hierarchii i elementu hierarchii, projekt może otworzyć drugi widok, jeśli można dołączyć do bazowego obiektu danych dokumentu. W przeciwnym razie projekt powinien używać wskaźnika do ramki okna widoku, aby można było połączyć istniejące okno.

   - Jeśli istnieje tylko obiekt danych dokumentu, projekt powinien określić, czy może on używać obiektu danych dokumentu dla widoku. Jeśli obiekt danych dokumentu jest zgodny, wykonaj kroki opisane w temacie [otwieranie edytora specyficznego dla projektu](../extensibility/how-to-open-project-specific-editors.md).

     Jeśli obiekt danych dokumentu nie jest zgodny, powinien zostać wyświetlony komunikat o błędzie informujący o tym, że plik jest aktualnie w użyciu. Ten błąd powinien być wyświetlany tylko w przypadkach przejściowych, na przykład wtedy, gdy plik jest kompilowany w tym samym czasie, użytkownik próbuje otworzyć plik przy użyciu edytora innego niż [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] podstawowy edytor tekstu. Podstawowy edytor tekstu może udostępniać obiekt danych dokumentu w kompilatorze.

3. Jeśli dokument nie jest otwarty, ponieważ nie ma obiektu danych dokumentu lub obiektu widoku dokumentu, wykonaj kroki opisane w temacie [otwieranie edytora specyficznego dla projektu](../extensibility/how-to-open-project-specific-editors.md).

## <a name="open-a-standard-editor"></a>Otwieranie edytora standardowego
 Aby otworzyć standardowy edytor dla pliku, który jest już otwarty, należy wykonać czynności opisane w poniższej procedurze.

### <a name="to-open-a-standard-editor-for-an-open-file"></a>Aby otworzyć standardowy edytor dla otwartego pliku

1. Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> .

     Ta metoda najpierw sprawdza, czy dokument nie jest jeszcze otwarty przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> . Jeśli dokument jest już otwarty, jego okno edytora zostanie przeznaczone.

2. Jeśli dokument nie jest otwarty, wykonaj kroki opisane w temacie [How to: Open Standard Editors](../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Zobacz też
- [Otwieranie i zapisywanie elementów projektu](../extensibility/internals/opening-and-saving-project-items.md)
- [Instrukcje: otwieranie edytorów specyficznych dla projektu](../extensibility/how-to-open-project-specific-editors.md)
- [Instrukcje: otwieranie edytorów standardowych](../extensibility/how-to-open-standard-editors.md)
