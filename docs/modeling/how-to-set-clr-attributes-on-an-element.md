---
title: 'Porady: ustawienie atrybutów CLR w elemencie'
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 49551a5e96e3c354b54b6b2ba7cedf1ba2ab4470
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90811204"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Porady: ustawienie atrybutów CLR w elemencie
Atrybuty niestandardowe są specjalnymi atrybutami, które mogą być dodawane do elementów domeny, kształtów, łączników i diagramów. Można dodać dowolny atrybut, który dziedziczy z `System.Attribute` klasy.

### <a name="to-add-a-custom-attribute"></a>Aby dodać atrybut niestandardowy

1. W **Eksploratorze DSL**wybierz element, do którego chcesz dodać atrybut niestandardowy.

2. W oknie **Właściwości** obok właściwości **atrybuty niestandardowe** kliknij ikonę Przeglądaj (**...**).

     Zostanie otwarte okno dialogowe **Edytowanie atrybutów** .

3. W kolumnie **Nazwa** kliknij **\<add attribute>** i wpisz nazwę atrybutu. Naciśnij klawisz ENTER.

4. Wiersz pod nazwą atrybutu zawiera nawiasy. W tym wierszu wpisz typ parametru dla atrybutu (na przykład `string` ), a następnie naciśnij klawisz ENTER.

5. W kolumnie **Nazwa właściwości** wpisz odpowiednią nazwę, na przykład `MyString` .

6. Kliknij przycisk **OK**.

     Właściwość **atrybuty niestandardowe** wyświetla teraz atrybut w następującym formacie:

     `[`*AttributeName* `(` *Parametrname* `=` *Typ*`)]`

## <a name="see-also"></a>Zobacz też

- [narzędzia języka specyficznego dla domeny słownik](/previous-versions/bb126564(v=vs.100))