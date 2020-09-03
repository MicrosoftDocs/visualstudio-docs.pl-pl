---
title: Opcje, Edytor tekstu, C#, IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Intellisense
helpviewer_keywords:
- IntelliSense [J#], options
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1e3f4df9a7a885245e40f7e9fec1b0da207ada39
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662299"
---
# <a name="options-text-editor-c-intellisense"></a>Opcje, edytor tekstu, C#, IntelliSense
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Strona właściwości **IntelliSense** służy do modyfikowania ustawień, które mają wpływ na zachowanie funkcji IntelliSense dla języka Visual C#. Aby uzyskać dostęp do strony właściwości **IntelliSense** , kliknij **opcję Opcje** w **menu Narzędzia** , a następnie kliknij pozycję **C#** w folderze **Edytor tekstu** , a następnie kliknij pozycję **IntelliSense.**

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 Strona właściwości **IntelliSense** zawiera następujące właściwości:

## <a name="completion-lists"></a>Listy uzupełniania
 **Pokaż listę uzupełniania po wpisaniu znaku** Po wybraniu tej opcji funkcja IntelliSense automatycznie wyświetla listę uzupełniania po rozpoczęciu wpisywania. Gdy ta opcja nie jest zaznaczona, ukończenie funkcji IntelliSense jest nadal dostępne w menu **IntelliSense** lub przez NACIŚNIĘCIE klawiszy CTRL + SPACJA.

 **Umieść słowa kluczowe w listach uzupełniania** Po wybraniu tej opcji technologia IntelliSense dodaje do listy uzupełniania słowa kluczowe języka C#, na przykład [klasy](https://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690).

 **Umieszczanie fragmentów kodu na listach uzupełniania** Po wybraniu tej opcji technologia IntelliSense dodaje aliasy dla fragmentów kodu C# do listy uzupełniania. W przypadku, gdy alias fragmentu kodu jest taki sam jak słowo kluczowe, na przykład, [Klasa](https://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690), słowo kluczowe jest zastępowane skrótem. Aby uzyskać więcej informacji, zobacz [fragmenty kodu Visual C#](../../ide/visual-csharp-code-snippets.md).

## <a name="selection-in-completion-lists"></a>Wybór na listach uzupełniania
 **Zatwierdzone przez wpisanie następujących znaków:** Określa wszystkie znaki, które wykonują automatyczne uzupełnianie IntelliSense dla wybranego elementu na liście uzupełniania po wpisaniu.

 **Zatwierdzone przez wciśnięcie klawisza spacji** Określa, aby dołączyć akcję naciskając klawisz spacji w celu wykonania automatycznego ukończenia IntelliSense dla wybranego elementu na liście uzupełniania.

 **Dodaj nowy wiersz przy klawiszu Enter na końcu w pełni wpisanego wyrazu** Określa, że po wpisaniu wszystkich znaków dla wpisu na liście uzupełniania, a następnie naciśnięciu klawisza ENTER, nowy wiersz zostanie utworzony automatycznie, a kursor zostanie przeniesiony do nowego wiersza.

 Na przykład, jeśli wpiszesz, `else` a następnie naciśniesz klawisz ENTER, w edytorze zostanie wyświetlony następujący komunikat:

 `else`

 `|` (Lokalizacja kursora)

 Jeśli jednak wpiszesz polecenie, `el` a następnie naciśniesz klawisz ENTER, w edytorze zostanie wyświetlony następujący komunikat:

 `else|` (Lokalizacja kursora)

## <a name="intellisense-member-selection"></a>Wybór elementu członkowskiego IntelliSense
 **Wstępnie wybiera ostatnio używany element członkowski** Po wybraniu tej opcji funkcja IntelliSense wstępnie wybiera elementy członkowskie, które były ostatnio zaznaczone w polu Członkowie listy podręcznej w celu automatycznego uzupełniania nazw obiektów podczas bieżącej sesji w zintegrowanym środowisku programistycznym (IDE). Historia ostatnio używanych elementów członkowskich jest czyszczona między poszczególnymi sesjami w IDE. Aby uzyskać więcej informacji, zobacz [IntelliSense dla ostatnio używanych elementów członkowskich](../../misc/intellisense-for-most-recently-used-members.md).

## <a name="see-also"></a>Zobacz też
 [Ogólne, środowisko, Opcje okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md) [Komentarze dokumentacji XML](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199) [przy użyciu technologii IntelliSense](../../ide/using-intellisense.md)
