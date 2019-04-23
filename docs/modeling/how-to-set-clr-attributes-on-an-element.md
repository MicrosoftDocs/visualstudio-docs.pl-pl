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
ms.openlocfilehash: 8954aa6a42e743617080bb6918508273c1dd9528
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60089110"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Instrukcje: Ustawienie atrybutów CLR w elemencie
Atrybuty niestandardowe są specjalne atrybuty, które mogą być dodawane do elementy domeny, kształty, łączników i diagramy. Możesz dodać dowolny atrybut, który dziedziczy z `System.Attribute` klasy.

### <a name="to-add-a-custom-attribute"></a>Aby dodać atrybut niestandardowy

1. W **Eksplorator DSL**, wybierz element, do którego chcesz dodać atrybut niestandardowy.

2. W **właściwości** okna, obok **atrybuty niestandardowe** właściwości, kliknij przycisk Przeglądaj (**...** ) ikona.

     **Edycja atrybutów** zostanie otwarte okno dialogowe.

3. W **nazwa** kolumny, kliknij przycisk  **\<Dodaj atrybut >** i wpisz nazwę swojej atrybutu. Naciśnij klawisz ENTER.

4. Wiersz pod nazwą atrybutu zawiera nawiasy. W tym wierszu typu parametru atrybutu (na przykład `string`), a następnie naciśnij klawisz ENTER.

5. W **właściwości Name** kolumny, wpisz odpowiednią nazwę, na przykład `MyString`.

6. Kliknij przycisk **OK**.

     **Atrybuty niestandardowe** właściwości wyświetla teraz atrybutu w następującym formacie:

     `[` *AttributeName* `(` *ParameterName* `=` *typu* `)]`

## <a name="see-also"></a>Zobacz też

- [Słownik narzędzi języka specyficznego dla domeny](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)