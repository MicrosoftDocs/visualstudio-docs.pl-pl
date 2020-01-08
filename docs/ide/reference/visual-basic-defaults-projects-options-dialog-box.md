---
title: Domyślne ustawienia programu Visual Basic, Projekty, okno dialogowe Opcje
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.VBDefaults
helpviewer_keywords:
- Option Explicit statement, setting in the IDE
- Option Compare statement, setting in the IDE
- Option Strict statement, setting in the IDE
ms.assetid: 2465cd9d-18b6-4c4a-b1ea-86dbab23fc79
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f33dd9b19297811597be406337d70392904e6e44
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596389"
---
# <a name="visual-basic-defaults-projects-options-dialog-box"></a>Domyślne ustawienia programu Visual Basic, Projekty, okno dialogowe Opcje
Określa ustawienia domyślne dla opcji projektu Visual Basic. Po utworzeniu nowego projektu określone instrukcje opcji zostaną dodane do nagłówka projektu w edytorze kodu. Opcje stosują się do wszystkich projektów Visual Basic.

Aby uzyskać dostęp do tego okna dialogowego, w menu **Narzędzia** kliknij pozycję **Opcje**, rozwiń folder **projekty i rozwiązania** , a następnie kliknij pozycję **domyślne ustawienia języka vb**.

 **Option Explicit**

Ustawia wartość domyślną kompilatora, tak aby jawne deklaracje zmiennych są wymagane. Domyślnie **opcja Explicit** jest ustawiona na wartość **włączone**. Aby uzyskać więcej informacji, zobacz [/optionexplicit —](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit).

 **Option Strict**

Ustawia wartość domyślną kompilatora, tak aby jawne konwersje zawężające są wymagane i późne wiązanie jest niedozwolone. Domyślnie ustawienie **Option Strict** jest **wyłączone**. Aby uzyskać więcej informacji, zobacz [/optionstrict —](/dotnet/visual-basic/reference/command-line-compiler/optionstrict).

 **Option Compare**

Ustawia domyślny kompilator dla porównań ciągów: binarny (z uwzględnieniem wielkości liter) lub tekst (bez uwzględniania wielkości liter). Domyślnie **opcja Porównaj** jest ustawiona na wartość **binarną**. Aby uzyskać więcej informacji, zobacz [/optioncompare —](/dotnet/visual-basic/reference/command-line-compiler/optioncompare).

 **Option Infer**

Ustawia wartość domyślną kompilatora dla wnioskowania o typie lokalnym. Domyślnie **opcja wnioskowanie** jest ustawiona na wartość **włączone** dla nowo utworzonych projektów i **wyłączone** dla zmigrowanych projektów utworzonych we wcześniejszych wersjach Visual Basic. Aby uzyskać więcej informacji, zobacz [/optioninfer —](/dotnet/visual-basic/reference/command-line-compiler/optioninfer).

## <a name="see-also"></a>Zobacz także

- [Rozwiązania i projekty](../../ide/solutions-and-projects-in-visual-studio.md)
