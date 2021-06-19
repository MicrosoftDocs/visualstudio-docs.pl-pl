---
title: 'Porady: ustawienie atrybutów CLR w elemencie'
description: Dowiedz się, jak dodać dowolny atrybut dziedziczący z klasy System.Attribute.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b11a6bd4a04bdb469cdf5c2fe2d7b78e0c0fe29a
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387336"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Porady: ustawienie atrybutów CLR w elemencie
Atrybuty niestandardowe to atrybuty specjalne, które można dodawać do elementów domeny, kształtów, łączników i diagramów. Możesz dodać dowolny atrybut dziedziczący z `System.Attribute` klasy .

### <a name="to-add-a-custom-attribute"></a>Aby dodać atrybut niestandardowy

1. W **Eksploratorze DSL** wybierz element, do którego chcesz dodać atrybut niestandardowy.

2. W **oknie** Właściwości obok właściwości **Atrybuty niestandardowe** kliknij ikonę Przeglądaj (**...**).

     Edytowanie **atrybutów zostanie otwarte** okno dialogowe.

3. W kolumnie **Nazwa** kliknij **\<add attribute>** i wpisz nazwę atrybutu. Naciśnij klawisz ENTER.

4. Wiersz pod nazwą atrybutu zawiera nawiasy. W tym wierszu wpisz typ parametru dla atrybutu (na przykład ), a `string` następnie naciśnij klawisz ENTER.

5. W kolumnie **Właściwość nazwy** wpisz odpowiednią nazwę, na przykład `MyString` .

6. Kliknij przycisk **OK**.

     Właściwość **Atrybuty niestandardowe** wyświetla teraz atrybut w następującym formacie:

     `[`*Nazwa atrybutu* `(` *Nazwa_parametru* `=` *Typ*`)]`

## <a name="see-also"></a>Zobacz też

- [narzędzia języka specyficznego dla domeny słownika](/previous-versions/bb126564(v=vs.100))