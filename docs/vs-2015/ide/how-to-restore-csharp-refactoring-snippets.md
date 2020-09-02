---
title: 'Instrukcje: Przywracanie fragmentów kodu w języku C# | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- unsafe expansion
- expansions, unsafe
ms.assetid: 12114273-7f2f-43d0-abcb-2d4711a3a68d
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6ae3f1d74a482192d3782aaa87baa816694abcf4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670784"
---
# <a name="how-to-restore-c-refactoring-snippets"></a>Porady: przywracanie refaktoryzowanych wstawek kodu C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Operacje refaktoryzacji języka C# polegają na fragmentach kodu znalezionych w następującym katalogu:

 *Katalog instalacyjny*\Microsoft Visual Studio 14.0 \ VC # \Snippets \\ *Identyfikator języka*\Refactoring

 Jeśli ten katalog refaktoryzacji lub wszystkie pliki w tym katalogu zostaną usunięte lub uszkodzone, operacje refaktoryzacji w języku C# mogą nie funkcjonować w środowisku IDE. Poniższe procedury mogą pomóc przywrócić fragmenty kodu refaktoryzacji języka C#.

### <a name="to-verify-c-refactoring-snippets-are-available-through-the-code-snippet-manager"></a>Aby sprawdzić fragmenty kodu refaktoryzacji w języku C#, można uzyskać za pomocą narzędzia Code fragment

1. W menu **Narzędzia** wybierz pozycję **Menedżer fragmentów kodu**.

2. W oknie dialogowym **Menedżer fragmentów kodu** wybierz pozycję **Visual C#** z listy rozwijanej **Język** .

     Folder **refaktoryzacji** powinien pojawić się na liście folderów widoku drzewa.

### <a name="to-restore-refactoring-see-comment-in-code-snippet-manager"></a>Aby przywrócić refaktoryzację, zobacz komentarz w Menedżerze fragmentów kodu

1. Jeśli folder **refaktoryzacji** nie jest wyświetlany na liście folderów widoku drzewa Menedżera fragmentów kodu, następnie użyj tej procedury, aby dodać fragmenty kodu refaktoryzacji do Menedżera fragmentów kodów.

2. W menu **Narzędzia** wybierz pozycję **Menedżer fragmentów kodu**.

3. W oknie dialogowym **Menedżer fragmentów kodu** wybierz pozycję **Visual C#** z listy rozwijanej **Język** .

4. Kliknij pozycję **Dodaj**. Zostanie wyświetlone okno dialogowe **katalog fragmentów kodu** , w którym można znaleźć i określić katalog, który zostanie dodany z powrotem do Menedżera fragmentów kodu.

5. Zlokalizuj folder **refaktoryzacji** , którego ścieżką do katalogu jest:

     *Katalog instalacyjny*\Microsoft Visual Studio 14.0 \ VC # \Snippets \\ *Identyfikator języka*\Refactoring

     Rzeczywista ścieżka jest podobna do następującej w przypadku instalacji domyślnej:

     C:\Program Files\Microsoft Visual Studio 14.0 \ VC # \Snippets\1033\Refactoring.

6. Kliknij przycisk **Otwórz** w **katalogu fragmenty kodu** , a następnie kliknij przycisk **OK** w Menedżerze fragmentów kodu.

## <a name="see-also"></a>Zobacz też
 [Fragmenty kodu](../ide/code-snippets.md) w [języku Visual C# kodu](../ide/visual-csharp-code-snippets.md) [refaktoryzacji (C#)](../csharp-ide/refactoring-csharp.md)
