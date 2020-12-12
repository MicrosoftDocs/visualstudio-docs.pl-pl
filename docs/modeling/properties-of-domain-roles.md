---
title: Właściwości ról w domenie
description: Zapoznaj się z właściwościami skojarzonymi z rolą domeny, takimi jak typ kolekcji, atrybuty niestandardowe i jest właściwością umożliwia przeglądania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6dda8e7c5538b0517c181a451072c4f8a9544965
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362343"
---
# <a name="properties-of-domain-roles"></a>Właściwości ról w domenie
Właściwości w poniższej tabeli są skojarzone z rolą domeny. Aby uzyskać informacje na temat ról domeny, zobacz [Opis modeli, klas i relacji](../modeling/understanding-models-classes-and-relationships.md). Aby uzyskać więcej informacji na temat sposobu korzystania z tych właściwości, zobacz [Dostosowywanie i rozszerzanie języka Domain-Specific](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Właściwość|Opis|Domyślny|
|-|-|-|
|Typ kolekcji|Jeśli ta rola ma liczebność równą 0.. * lub 1.. \* , ta właściwość dostosowuje typ ogólny, który jest używany do przechowywania kolekcji linków.|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> jest używany|
|Atrybuty niestandardowe|Atrybuty określone w tym miejscu zostaną dodane jako atrybuty do wygenerowanej klasy kodu.|<brak\>|
|Jest właściwością umożliwia przeglądania|Jeśli `True` , i, Jeśli liczebność relacji wynosi 0.. 1 lub 1.. 1, właściwość roli może być przeglądana przez użytkownika w oknie **Właściwości** . Właściwość wyświetla nazwę elementu na drugim końcu łącza relacji.|`True`|
|Jest generatorem właściwości|Jeśli `True` Właściwość roli jest generowana dla tej roli, której można użyć do przechodzenia między relacjami w kodzie programu. W przypadku ustawienia tego elementu false, można przechodzić w sposób mniej wydajny przy użyciu metod statycznych relacji domeny.|`True`|
|Modyfikator dostępu metody pobierającej właściwości|Modyfikator dostępu dla metody pobierającej dla wygenerowanej właściwości ( `public` , `internal` ,, `private` `protected` lub `protected internal` ).|`public`|
|Modyfikator dostępu metody ustawiającej właściwość|Modyfikator dostępu dla metody ustawiającej dla wygenerowanej właściwości ( `public` , `internal` , `private` , `protected` lub `protected internal` ).|`public`|
|Kardynalność|Liczba elementów modelu, które mogą odgrywać odwrotną rolę ( `0..1` , `1..1` , `0..*` lub `1..*` ). Jeśli liczebność jest `0..*` lub `1..*` , wówczas wygenerowana właściwość reprezentuje kolekcję; w przeciwnym razie wygenerowana właściwość reprezentuje pojedynczy element modelu.|Zależy od typu relacji i tego, czy jest to rola źródłowa lub docelowa w relacji.|
|Nazwa|Nazwa roli domeny. Ta właściwość nie może zawierać odstępów.|Nazwa klasy domeny obiektu pełniącego rolę dla tej roli.|
|Propaguje kopię|`DoNotPropagateCopy` -Skopiowany obiekt pełniący rolę nie będzie miał kopii tego linku.<br /><br /> `PropagateCopyToLinkOnly` -Skopiowane łącze prowadzi do istniejącego przeciwległego obiektu pełniącego rolę.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer` -Skopiowane łącze wskazuje kopię przeciwległego obiektu pełniącego rolę.|`PropagateCopyToLinkAndOppositeRolePlayer` dla ról źródłowych osadzania.<br /><br /> `DoNotPropagateCopy` w przypadku innych ról.<br /><br /> Aby uzyskać więcej informacji, zobacz [Dostosowywanie zachowania kopiowania](../modeling/customizing-copy-behavior.md)|
|Propagowanie usuwania|`True` Aby usunąć element, który odgrywa tę rolę po usunięciu skojarzonego linku.|`True` dla obiektu docelowego roli osadzania.<br /><br /> `False` w przypadku innych ról.|
|Nazwa właściwości|Nazwa właściwości wygenerowanej w kodzie obiektu pełniącego rolę. Ta nazwa nie może zawierać odstępów.|Nazwa przeciwległej roli, jeśli ta rola ma wartość zero-do-jednego lub liczebność jeden-do-jednego; w przeciwnym razie nazwa w liczbie mnogiej roli odwrotnej.|
|Obiekt pełniący rolę|Klasa domeny elementu, który może odtwarzać tę rolę w relacji. Ta właściwość jest tylko do odczytu.|Klasa domeny obiektu pełniącego rolę dla tej roli.|
|Uwagi|Nieformalne uwagi, które są skojarzone z rolą domeny.|<brak\>|
|Kategoria|Kategoria, pod którą wygenerowana właściwość pojawia się w oknie **Właściwości** w wygenerowanym projektancie. Jeśli ta właściwość jest pusta, wygenerowana właściwość zostanie wyświetlona w obszarze Kategoria **różne**|<brak\>|
|Opis|Opis używany do dokumentowania kodu i jest używany w interfejsie użytkownika wygenerowanego projektanta.<br /><br /> Opis jest wyświetlany w etykietce narzędzia IntelliSense dla wygenerowanej właściwości klasy obiektu pełniącego rolę.|`Description for`*pełna nazwa roli*|
|Nazwa wyświetlana|Nazwa wyświetlana w wygenerowanym projektancie dla roli domeny.|Skorygowana wartość właściwości Nazwa.|
|Słowo kluczowe pomocy|Opcjonalne słowo kluczowe, które jest używane do indeksowania pomocy klawisza F1 dla roli domeny.|\<none>|
|Nazwa wyświetlana właściwości|Nazwa wyświetlana w wygenerowanym projektancie dla wygenerowanej właściwości roli.|Wartość skorygowana właściwości Nazwa właściwości.|

> [!NOTE]
> Wartość domyślna nazwy wyświetlanej jest oparta na wartości skojarzonej właściwości przez Wstawianie spacji przed każdym wielkie litery, które jest poprzedzone znakiem małych liter i nie następuje po nim kolejnego znaku Case.

## <a name="see-also"></a>Zobacz też

- [Właściwości relacji domeny](../modeling/properties-of-domain-relationships.md)