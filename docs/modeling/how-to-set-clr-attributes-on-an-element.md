---
title: 'Porady: ustawienie atrybutów CLR w elemencie'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f943f9713e4432f0b06242a2f66acae6b390e5cc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748371"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Porady: ustawienie atrybutów CLR w elemencie
Atrybuty niestandardowe są specjalnymi atrybutami, które mogą być dodawane do elementów domeny, kształtów, łączników i diagramów. Można dodać dowolny atrybut, który dziedziczy z klasy `System.Attribute`.

### <a name="to-add-a-custom-attribute"></a>Aby dodać atrybut niestandardowy

1. W **Eksploratorze DSL**wybierz element, do którego chcesz dodać atrybut niestandardowy.

2. W oknie **Właściwości** obok właściwości **atrybuty niestandardowe** kliknij ikonę Przeglądaj ( **...** ).

     Zostanie otwarte okno dialogowe **Edytowanie atrybutów** .

3. W kolumnie **Nazwa** kliknij **\<add atrybut >** i wpisz nazwę atrybutu. Naciśnij klawisz ENTER.

4. Wiersz pod nazwą atrybutu zawiera nawiasy. W tym wierszu wpisz typ parametru dla atrybutu (na przykład `string`), a następnie naciśnij klawisz ENTER.

5. W kolumnie **Nazwa właściwości** wpisz odpowiednią nazwę, na przykład `MyString`.

6. Kliknij przycisk **OK**.

     Właściwość **atrybuty niestandardowe** wyświetla teraz atrybut w następującym formacie:

     `[` *AttributeName* `(` *ParameterName* `=` *Typ* `)]`

## <a name="see-also"></a>Zobacz także

- [narzędzia języka specyficznego dla domeny słownik](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)