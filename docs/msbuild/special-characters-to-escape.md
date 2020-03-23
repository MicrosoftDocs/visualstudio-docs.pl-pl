---
title: Znaki specjalne do ucieczki | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- special characters to escape
- msbuild, special characters to escape
ms.assetid: 5b5172c3-41e4-4f38-a16f-2aeac831a5fc
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1b17ded468e262d4f636ed5494081adab7b8c5f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632254"
---
# <a name="special-characters-to-escape"></a>Znaki specjalne do ucieczki

Znaki specjalne muszą być zmienione tylko wtedy, gdy mają specjalne znaczenie w kontekście, w którym są używane. Na przykład gwiazdka (*) jest znakiem specjalnym tylko w atrybutach "Uwzględnij" i "Wyklucz" <xref:Microsoft.Build.Tasks.CreateItem>definicji elementu lub w wywołaniu . We wszystkich innych przypadkach gwiazdka jest traktowana jako gwiazdka dosłowna. Chociaż nie trzeba uciekać gwiazdki wszędzie w plikach projektu, robi to nie szkodzi.

 Zamiast znaku specjalnego\<należy użyć notacji % xx \<>, gdzie xx> reprezentuje wartość szesnastkową znaku ASCII. Na przykład, aby użyć gwiazdki (*) jako znaku literału, użyj wartości `%2A`.

 Pełna lista znaków specjalnych do ucieczki jest następująca:

|Znak|Opis|
|---------------|-----------------|
|%|Znak procentu, używany do odwoływania się do metadanych.|
|$|Znak dolara, używany do odwoływania się do właściwości.|
|@|Na znak, używany do odwoływania się do list elementów.|
|(|Otwórz nawias, używany na listach.|
|)|Zamknij nawias, używany na listach.|
|;|Średnik, separator listy.|
|?|Znak zapytania, symbol wieloznaczny opisujący specyfikację pliku w sekcji Dołącz/Wyklucz element.|
|*|Gwiazdka, symbol wieloznaczny opisujący specyfikację pliku w sekcji Dołącz/Wyklucz element.|

> [!NOTE]
> W niektórych scenariuszach może być konieczne uniknięcie znaków cudzysłowu ("), na przykład podczas korzystania z `Exec` zadania.

## <a name="see-also"></a>Zobacz też

- [Jak: Ucieczka znaków specjalnych w MSBuild](../msbuild/how-to-escape-special-characters-in-msbuild.md)
- [Odwołanie do budynku MSBuild](../msbuild/msbuild-reference.md)
