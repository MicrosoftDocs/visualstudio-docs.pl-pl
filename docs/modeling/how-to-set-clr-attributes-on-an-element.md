---
title: 'Instrukcje: Ustawienie atrybutów CLR w elemencie'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 54b4340fe72552f3287a5c6ebec55c9c9d326ac1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54932275"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Instrukcje: Ustawienie atrybutów CLR w elemencie
Atrybuty niestandardowe są specjalne atrybuty, które mogą być dodawane do elementy domeny, kształty, łączników i diagramy. Możesz dodać dowolny atrybut, który dziedziczy z `System.Attribute` klasy.

### <a name="to-add-a-custom-attribute"></a>Aby dodać atrybut niestandardowy

1.  W **Eksplorator DSL**, wybierz element, do którego chcesz dodać atrybut niestandardowy.

2.  W **właściwości** okna, obok **atrybuty niestandardowe** właściwości, kliknij przycisk Przeglądaj (**...** ) ikona.

     **Edycja atrybutów** zostanie otwarte okno dialogowe.

3.  W **nazwa** kolumny, kliknij przycisk  **\<Dodaj atrybut >** i wpisz nazwę swojej atrybutu. Naciśnij klawisz ENTER.

4.  Wiersz pod nazwą atrybutu zawiera nawiasy. W tym wierszu typu parametru atrybutu (na przykład `string`), a następnie naciśnij klawisz ENTER.

5.  W **właściwości Name** kolumny, wpisz odpowiednią nazwę, na przykład `MyString`.

6.  Kliknij przycisk **OK**.

     **Atrybuty niestandardowe** właściwości wyświetla teraz atrybutu w następującym formacie:

     `[` *AttributeName* `(` *ParameterName* `=` *typu* `)]`

## <a name="see-also"></a>Zobacz też

- [Słownik narzędzi języka specyficznego dla domeny](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)