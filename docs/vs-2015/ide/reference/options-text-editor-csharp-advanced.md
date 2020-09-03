---
title: Opcje, Edytor tekstu, C#, zaawansowane | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Advanced
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.CSharp.Advanced
helpviewer_keywords:
- XML comments
- XML documentation, generating
- outlining options [C#]
- outlining options [J#]
- XML documentation, creating
ms.assetid: 947f9d9a-b0f3-408d-9866-d82895bcee31
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4f2d11e78c2402a6541bc87748ed6ba348ba80fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662320"
---
# <a name="options-text-editor-c-advanced"></a>Opcje, edytor tekstu, C#, zaawansowane
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

To okno dialogowe służy do modyfikowania ustawień formatowania edytora, refaktoryzacji kodu i komentarzy dokumentacji XML dla języka Visual C#. Aby uzyskać dostęp do tego okna dialogowego, kliknij opcję **Opcje** w menu **Narzędzia** , rozwiń folder **Edytor tekstu** , rozwiń węzeł **C#**, a następnie kliknij pozycję **Zaawansowane**.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="outlining"></a>Tworzenie konspektu
 Wejdź w tryb konspektu, gdy pliki są otwierane po zaznaczeniu, automatycznie podkreśla plik kodu, który tworzy zwijane bloki kodu. Przy pierwszym otwarciu pliku, bloki #regions bloków i nieaktywnych bloków kodu są zwijane.

## <a name="editor-help"></a>Pomoc edytora
 Błędy podkreślenia w edytorze identyfikują błędy kompilacji w kodzie. Po wybraniu tej opcji faliste podkreślenie pojawiają się w kolorze, który ma określone znaczenie:

- Błędy analizy są czerwone.

- Błędy kompilacji są niebieskie.

- Ostrzeżenia kompilacji są zielone.

- Nieprawidłowa [Edycja Edytuj i Kontynuuj](../../debugger/edit-and-continue.md) edycji są purpurowe.

  Przesuń wskaźnik myszy nad podkreślony segment kodu, aby wyświetlić etykietkę narzędzia z informacjami o błędzie.

  Pokaż błędy semantyczne na żywo identyfikują pewne błędy kompilacji bez jawnej kompilacji, na przykład deklarując i używając nieznanego typu lub odwołujący się do nieznanej właściwości.

  Wyróżnij odwołania do symbolu pod kursorem, gdy kursor jest umieszczony wewnątrz symbolu lub po kliknięciu symbolu, wszystkie wystąpienia tego symbolu w pliku kodu są wyróżnione.

## <a name="refactoring"></a>Refaktoryzacja
 Sprawdź wyniki refaktoryzacji wyświetla okno dialogowe **wyniki weryfikacji** przy próbie refaktoryzacji kodu, który zawiera błędy kompilacji, lub gdy Refaktoryzacja spowoduje, że odwołanie do kodu ma być powiązane z innym względem oryginalnego powiązania.

 Ostrzegaj w przypadku elementów członkowskich z odwołaniami wygenerowanymi przez kompilator wyświetla okno dialogowe ostrzeżenia podczas próby refaktoryzacji elementu członkowskiego, który ma taką samą nazwę jak odwołanie wygenerowane przez kompilator.

## <a name="xml-documentation-comments"></a>Komentarze dokumentacji XML
 Generuj komentarze dokumentacji XML dla///po zaznaczeniu wstawiaj \<summary> automatycznie Tagi początkowe i końcowe dla komentarzy dokumentacji XML po wpisaniu wprowadzania///wprowadzenia komentarza. Aby uzyskać więcej informacji na temat dokumentacji XML, zobacz [Komentarze dokumentacji XML](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199).

## <a name="implement-interface"></a>Implementowanie interfejsu
 Przestrzenny wygenerowany kod z #region wstawia \<*interface name*> element członkowski #region wokół metod, gdy jest używany interfejs implementujący interfejs lub implementowany jest jawnie.

## <a name="organize-usings"></a>Organizuj użycia
 Umieść dyrektywy "system" jako pierwsze podczas sortowania przy użyciu, gdy `System` są zaznaczone, dyrektywy using są wyświetlane przed innymi dyrektywami using. Aby uzyskać więcej informacji, zobacz [Sortowanie using](../../misc/sort-usings.md).

## <a name="see-also"></a>Zobacz też
 [Komentarze dokumentacji XML](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199) [Ustawianie opcji edytora specyficznych dla języka](../../ide/reference/setting-language-specific-editor-options.md) [Visual C# IntelliSense](../../ide/visual-csharp-intellisense.md)
