---
title: Opcje, Edytor tekstu, wszystkie języki, karty | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.ResJSON.Tabs
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.All_Languages.Tabs
helpviewer_keywords:
- indents, Code Editor
- Code Editor, default behavior
- tabs, setting in Code Editor
- All Languages Text Editor Options dialog box
- editors, Code Editor
- Code Editor, indenting
- Code Editor, tabs
ms.assetid: 7e208e1d-5e3a-4bf7-a27b-4417e3e049c7
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4cb670ab52e321f15c5b009c66ca40623409f10a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662385"
---
# <a name="options-text-editor-all-languages-tabs"></a>Opcje, edytor tekstu, wszystkie języki, karty
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

To okno dialogowe umożliwia zmianę domyślnego zachowania edytora kodu. Te ustawienia mają zastosowanie również do innych edytorów w oparciu o Edytor kodu, taki jak widok źródła projektanta HTML. Aby wyświetlić te opcje, wybierz opcję **Opcje** z menu **Narzędzia** . W folderze **Edytor tekstu** rozwiń podfolder **wszystkie języki** , a następnie wybierz pozycję **karty**.

> [!CAUTION]
> Ta strona służy do ustawiania opcji domyślnych dla wszystkich języków deweloperskich. Pamiętaj, że Resetowanie opcji w tym oknie dialogowym spowoduje zresetowanie opcji tabulatorów we wszystkich językach do wybranych opcji. Aby zmienić opcje edytora tekstu dla tylko jednego języka, rozwiń podfolder dla tego języka i wybierz jego strony opcji.

 Jeśli na stronach opcji kart są wybrane różne ustawienia dla określonych języków programowania, komunikat "Ustawienia wcięć dla pojedynczych formatów tekstu kolidują ze sobą" jest wyświetlany w przypadku różnych opcji **wcięć** ; a komunikat "ustawienia tabulacji dla pojedynczych formatów tekstu kolidują ze sobą," jest wyświetlany dla różnych opcji **tabulacji** . Na przykład, to przypomnienie jest wyświetlane, jeśli wybrano opcję **inteligentnego tworzenia wcięć** dla Visual Basic, ale dla wizualizacji C++jest wybrane **wcięcie bloku** .

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="indenting"></a>Wcięcia
 Brak, gdy to zaznaczone, nowe wiersze nie mają wcięcia. Punkt wstawiania zostanie umieszczony w pierwszej kolumnie nowego wiersza.

 Zablokuj, gdy zaznaczone, nowe wiersze są automatycznie wcięte. Punkt wstawiania jest umieszczany w tym samym punkcie początkowym co poprzedni wiersz.

 Inteligentne, gdy zaznaczone, nowe wiersze są pozycjonowane w celu dopasowania do kontekstu kodu, według innych ustawień formatowania kodu i Konwencji IntelliSense dla języka deweloperskiego. Ta opcja nie jest dostępna dla wszystkich języków deweloperskich.

 Na przykład wiersze ujęte w nawias klamrowy otwierającego ({) i zamykającego nawiasu klamrowego (}) mogą automatycznie powodować wcięcie dodatkowego tabulatora od pozycji wyrównanych nawiasów klamrowych.

## <a name="tabs"></a>Karty
 Rozmiar karty Ustawia odległość między tabulatorami. Wartość domyślna to cztery spacje.

 Wcięcie rozmiaru ustawia rozmiar w odstępach automatycznego wcięcia. Wartość domyślna to cztery spacje. Znaki tabulacji, znaki spacji lub oba zostaną wstawione w celu wypełnienia określonego rozmiaru.

 Wstawiaj spacje po zaznaczeniu, operacje wcięcia wstawiają tylko znaki spacji, a nie znaki TABULACJi. Jeśli **Rozmiar wcięcia** jest ustawiony na 5, na przykład po naciśnięciu klawisza TAB lub przycisku **Zwiększ wcięcie** na pasku narzędzi **formatowania** zostanie wstawionych pięć znaków spacji.

 Zachowaj karty po zaznaczeniu, aby zwiększyć liczbę znaków TABULACJi. Każdy znak TABULACJi wypełnia liczbę spacji określoną w polu **rozmiar karty**. Jeśli **Rozmiar wcięcia** nie jest parzystą wielokrotnością **rozmiaru karty**, znaki spacji są dodawane do wypełnienia różnic.

## <a name="see-also"></a>Zobacz też
 [Opcje, Edytor tekstu, wszystkie języki](../../ide/reference/options-text-editor-all-languages.md) [Ogólne, środowisko, Opcje — okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
