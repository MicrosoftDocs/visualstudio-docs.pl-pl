---
title: Opcje, Edytor tekstu, C#, IntelliSense | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4e5ca0c60511ee9537041f3a41f44a0e1f55b5a2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441363"
---
# <a name="options-text-editor-c-intellisense"></a>Opcje, edytor tekstu, C#, IntelliSense
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Użyj **IntelliSense** stronie właściwości, aby zmodyfikować ustawienia, które wpływają na działanie technologii IntelliSense dla języka Visual C#. Możesz uzyskać dostęp **IntelliSense** strony właściwości, klikając **opcje** na **narzędzia** menu, klikając **C#** w **Edytora tekstów** folder, a następnie klikając **IntelliSense.**  
  
> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 **IntelliSense** strona właściwości zawiera następujące właściwości:  
  
## <a name="completion-lists"></a>Listy uzupełniania  
 **Pokaż listę uzupełniania po wpisaniu znaku**  
 Gdy ta opcja jest zaznaczona, IntelliSense wyświetla automatycznie na liście uzupełniania po rozpoczęciu wpisywania. Gdy ta opcja nie jest zaznaczona, uzupełnianie przez funkcję IntelliSense są nadal dostępne z poziomu **IntelliSense** menu lub naciskając klawisze CTRL + SPACJA.  
  
 **Umieść słowa kluczowe w listach uzupełniania**  
 Gdy ta opcja jest zaznaczona, IntelliSense dodaje słowa kluczowe języka C#, na przykład [klasy](http://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690), na liście uzupełniania.  
  
 **Umieść fragmenty kodu w listach uzupełniania**  
 Gdy ta opcja jest zaznaczona, IntelliSense dodaje aliasy we fragmentach kodu języka C# na liście uzupełniania. W przypadku, gdy alias fragment kodu jest taka sama jak słowo kluczowe, na przykład [klasy](http://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690), słowo kluczowe zastępuje skrót. Aby uzyskać więcej informacji, zobacz [Visual C# — wstawki](../../ide/visual-csharp-code-snippets.md).  
  
## <a name="selection-in-completion-lists"></a>Wybór w listach uzupełniania  
 **Zatwierdzone, wpisując następujące znaki:**  
 Określa wszystkie znaki, które należy wykonać automatyczne uzupełnianie przez funkcję IntelliSense dla wybranego elementu na liście uzupełniania po wpisywania ich.  
  
 **Zatwierdzone, naciskając klawisz spacji**  
 Określa, aby uwzględnić akcji naciskając klawisz spacji, aby wykonać automatyczne uzupełnianie przez funkcję IntelliSense dla wybranego elementu na liście uzupełniania.  
  
 **Dodaj nowy wiersz po naciśnięciu klawisza enter na końcu pełnego wpisanego wyrazu**  
 Określa, że jeśli wpisz wszystkie znaki dla wpisu na liście uzupełniania, a następnie naciśnij klawisz ENTER, automatycznie tworzony jest nowy wiersz, i kursor przesuwa się do nowego wiersza.  
  
 Na przykład, jeśli wpiszesz `else` i naciśnij klawisz ENTER w edytorze pojawi się następujące:  
  
 `else`  
  
 `|` (Lokalizacja kursora)  
  
 Jednakże jeśli wpiszesz tylko `el` i naciśnij klawisz ENTER w edytorze pojawi się następujące:  
  
 `else|` (Lokalizacja kursora)  
  
## <a name="intellisense-member-selection"></a>Wybór elementów członkowskich IntelliSense  
 **Wybiera wstępne ostatnio używane elementu członkowskiego**  
 Gdy ta opcja jest zaznaczona, IntelliSense wstępnie wybiera elementy członkowskie zaznaczone niedawno w wyskakującym listę elementów członkowskich dla obiektów automatycznych uzupełnianie nazw, podczas bieżącej sesji w zintegrowanym środowisku programistycznym (IDE). Historia ostatnio używanych elementów członkowskich jest czyszczona między każdej sesji w środowisku IDE. Aby uzyskać więcej informacji, zobacz [technologii IntelliSense dla ostatnio używane członków](../../misc/intellisense-for-most-recently-used-members.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Ogólne, środowisko, okno dialogowe Opcje](../../ide/reference/general-environment-options-dialog-box.md)   
 [Komentarze dokumentacji XML](http://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199)   
 [Korzystanie z funkcji IntelliSense](../../ide/using-intellisense.md)
