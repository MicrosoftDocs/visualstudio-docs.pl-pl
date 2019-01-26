---
title: Domyślne ustawienia programu Visual Basic, Projekty, okno dialogowe Opcje
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.VBDefaults
helpviewer_keywords:
- Option Explicit statement, setting in the IDE
- Option Compare statement, setting in the IDE
- Option Strict statement, setting in the IDE
ms.assetid: 2465cd9d-18b6-4c4a-b1ea-86dbab23fc79
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a558fa33760645648b427c3f6cc95991d601c483
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54934507"
---
# <a name="visual-basic-defaults-projects-options-dialog-box"></a>Domyślne ustawienia programu Visual Basic, Projekty, okno dialogowe Opcje
Określa wartości domyślne dla opcji projektu języka Visual Basic. Po utworzeniu nowego projektu instrukcji określoną opcję zostaną dodane do nagłówka projektu w edytorze kodu. Opcje są stosowane do wszystkich projektów w języku Visual Basic.

 Dostęp do tego okna dialogowego w **narzędzia** menu, kliknij przycisk **opcje**, rozwiń węzeł **projekty i rozwiązania** folder, a następnie kliknij **VB domyślnie**.

 **Option Explicit**

 Ustawia domyślny kompilator jawnej deklaracji zmiennych są wymagane. Domyślnie **Option Explicit** ustawiono **na**. Aby uzyskać więcej informacji, zobacz [/optionexplicit —](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit).

 **Option Strict**

 Ustawia domyślny kompilator, tak, aby jawne konwersje zawężające są wymagane, a późne wiązanie jest niedozwolone. Domyślnie **Option Strict** ustawiono **poza**. Aby uzyskać więcej informacji, zobacz [/optionstrict —](/dotnet/visual-basic/reference/command-line-compiler/optionstrict).

 **Option Compare**

 Ustawia domyślny kompilator do porównywania ciągów znaków: plik binarny (z uwzględnieniem wielkości liter) lub tekst (bez uwzględniania wielkości liter.) Domyślnie **Option Compare** ustawiono **binarne**. Aby uzyskać więcej informacji, zobacz [/optioncompare —](/dotnet/visual-basic/reference/command-line-compiler/optioncompare).

 **Option Infer**

 Ustawia domyślną kompilatora wnioskowanie o typie lokalnym. Domyślnie **Option Infer** jest ustawiona na **na** dla nowo utworzonych projektów i do **poza** dla migrowanych projekty utworzone we wcześniejszych wersjach programu Visual Basic. Aby uzyskać więcej informacji, zobacz [/optioninfer —](/dotnet/visual-basic/reference/command-line-compiler/optioninfer).

## <a name="see-also"></a>Zobacz też

- [Rozwiązania i projekty](../../ide/solutions-and-projects-in-visual-studio.md)