---
title: Właściwości ról w domenie
description: Dowiedz się więcej o właściwościach skojarzonych z rolą domeny, takich jak Typ kolekcji, Atrybuty Niestandardowe i Czy można przeglądać właściwości.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 670704a86f0c149d26c7c869259c0f2f6bb75881
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385151"
---
# <a name="properties-of-domain-roles"></a>Właściwości ról w domenie
Właściwości w poniższej tabeli są skojarzone z rolą domeny. Aby uzyskać informacje o rolach domeny, zobacz [Opis modeli, klas i relacji.](../modeling/understanding-models-classes-and-relationships.md) Aby uzyskać więcej informacji na temat używania tych właściwości, zobacz Dostosowywanie i [rozszerzanie Domain-Specific języku](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Właściwość|Opis|Domyślne|
|-|-|-|
|Typ kolekcji|Jeśli ta rola ma liczebność 0,.* lub 1.. , ta właściwość dostosowuje typ ogólny używany do przechowywania \* kolekcji linków.|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> jest używany|
|Atrybuty niestandardowe|Atrybuty określone w tym miejscu zostaną dodane jako atrybuty do wygenerowanej klasy kodu.|<brak\>|
|Czy właściwość można przeglądać|Jeśli wartość to , a liczebność relacji to `True` 0..1 lub 1..1, właściwość roli może być przeglądana przez użytkownika w **oknie** Właściwości. Właściwość wyświetla nazwę elementu na drugim końcu linku relacji.|`True`|
|Is Property Generator|Jeśli , dla tej roli jest generowana właściwość roli, której można użyć do przechodzenia `True` relacji w kodzie programu. Jeśli ustawisz tę wartość false, możesz przechodzić przez relację w mniej wydajny sposób przy użyciu statycznych metod relacji domeny.|`True`|
|Modyfikator dostępu getter właściwości|Modyfikator dostępu dla getter dla wygenerowanej właściwości ( `public` , , , , lub `internal` `private` `protected` `protected internal` ).|`public`|
|Modyfikator dostępu ustawiającego właściwości|Modyfikator dostępu dla ustawiającego dla wygenerowanej właściwości ( `public` , , , lub `internal` `private` `protected` `protected internal` ).|`public`|
|Kardynalność|Liczba elementów modelu, które mogą odgrywać rolę przeciwną ( `0..1` `1..1` , , lub `0..*` `1..*` ). Jeśli liczebność to lub , wygenerowana właściwość reprezentuje kolekcję. W przeciwnym razie wygenerowana właściwość `0..*` `1..*` reprezentuje pojedynczy element modelu.|Zależy od typu relacji i od tego, czy jest to rola źródłowa, czy docelowa w relacji.|
|Nazwa|Nazwa roli domeny. Ta właściwość nie może zawierać białych znaków.|Nazwa klasy domeny odtwarzacza roli dla tej roli.|
|Propaguje kopię|`DoNotPropagateCopy` — Skopiowany odtwarzacz roli nie będzie miał kopii tego linku.<br /><br /> `PropagateCopyToLinkOnly` — Skopiowany link wskazuje istniejącego przeciwnego odtwarzacza roli.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer` — Skopiowany link wskazuje kopię przeciwnego odtwarzacza roli.|`PropagateCopyToLinkAndOppositeRolePlayer` dla ról źródłowych osadzania.<br /><br /> `DoNotPropagateCopy` w przypadku innych ról.<br /><br /> Aby uzyskać więcej informacji, zobacz [Dostosowywanie zachowania kopiowania](../modeling/customizing-copy-behavior.md)|
|Propaguje usuwanie|`True` aby usunąć element, który odgrywa tę rolę po usunięciu skojarzonego linku.|`True` dla obiektu docelowego roli osadzania.<br /><br /> `False` w przypadku innych ról.|
|Nazwa właściwości|Nazwa właściwości wygenerowanej w kodzie odtwarzacza roli. Ta nazwa nie może zawierać białych znaków.|Nazwa roli przeciwległej, jeśli ta rola ma liczebność od zera do jednego lub liczebność "jeden do jednego". w przeciwnym razie nazwa roli przeciwległej w liczbie mnogiej.|
|Role Player|Klasa domeny elementu, który może odgrywać tę rolę w relacji. Ta właściwość jest tylko do odczytu.|Klasa domeny odtwarzacza roli dla tej roli.|
|Uwagi|Notatki nieformalne skojarzone z rolą domeny.|<brak\>|
|Kategoria|Kategoria, w której wygenerowana właściwość pojawia się w **oknie Właściwości** w wygenerowanym projektancie. Jeśli ta właściwość jest pusta, wygenerowana właściwość pojawi się w kategorii **Misc**|<brak\>|
|Opis|Opis, który jest używany do dokumentować kod i jest używany w interfejsie użytkownika wygenerowanego projektanta.<br /><br /> Opis zostanie wyświetlony w etykietce narzędzia IntelliSense dla wygenerowanej właściwości klasy odtwarzacza roli.|`Description for`*pełna nazwa roli*|
|Nazwa wyświetlana|Nazwa wyświetlana w wygenerowanym projektancie roli domeny.|Dostosowana wartość właściwości Name.|
|Słowo kluczowe pomocy|Opcjonalne słowo kluczowe używane do indeksowania pomocy F1 dla roli domeny.|\<none>|
|Nazwa wyświetlana właściwości|Nazwa wygenerowanej właściwości roli wyświetlana w wygenerowanym projektancie.|Dostosowana wartość właściwości Nazwa właściwości.|

> [!NOTE]
> Wartość domyślna nazwy wyświetlanej jest oparta na skojarzonej wartości właściwości przez wstawienie spacji przed każdym znakiem wielkich liter poprzedzonym znakiem małe litery, a po którym nie następuje kolejny znak wielkich liter.

## <a name="see-also"></a>Zobacz też

- [Właściwości relacji domeny](../modeling/properties-of-domain-relationships.md)