---
title: Właściwości ról domeny | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
ms.assetid: 5a7bb18c-638e-45e8-9d79-9aa6a9e14b0e
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a0cddfb3d5c95e5636e9dac069106e3010bedff8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671464"
---
# <a name="properties-of-domain-roles"></a>Właściwości ról w domenie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Właściwości w poniższej tabeli są skojarzone z rolą domeny. Aby uzyskać informacje na temat ról domeny, zobacz [Opis modeli, klas i relacji](../modeling/understanding-models-classes-and-relationships.md). Aby uzyskać więcej informacji o sposobach korzystania z tych właściwości, zobacz [Dostosowywanie i rozszerzanie języka specyficznego dla domeny](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Właściwość|Opis|Domyślne|
|--------------|-----------------|-------------|
|Typ kolekcji|Jeśli ta rola ma liczebność równą 0.. * lub 1.. \* , ta właściwość dostosowuje typ ogólny, który jest używany do przechowywania kolekcji linków.|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> jest używany|
|Atrybuty niestandardowe|Atrybuty określone w tym miejscu zostaną dodane jako atrybuty do wygenerowanej klasy kodu.|\<none>|
|Jest właściwością umożliwia przeglądania|Jeśli `True` , i, Jeśli liczebność relacji wynosi 0.. 1 lub 1.. 1, właściwość roli może być przeglądana przez użytkownika w oknie **Właściwości** . Właściwość wyświetla nazwę elementu na drugim końcu łącza relacji.|`True`|
|Jest generatorem właściwości|Jeśli `True` Właściwość roli jest generowana dla tej roli, której można użyć do przechodzenia między relacjami w kodzie programu. W przypadku ustawienia tego elementu false, można przechodzić w sposób mniej wydajny przy użyciu metod statycznych relacji domeny.|`True`|
|Modyfikator dostępu metody pobierającej właściwości|Modyfikator dostępu dla metody pobierającej dla wygenerowanej właściwości ( `public` , `internal` ,, `private` `protected` lub `protected internal` ).|`public`|
|Modyfikator dostępu metody ustawiającej właściwość|Modyfikator dostępu dla metody ustawiającej dla wygenerowanej właściwości ( `public` , `internal` , `private` , `protected` lub `protected internal` ).|`public`|
|Kardynalność|Liczba elementów modelu, które mogą odgrywać odwrotną rolę ( `0..1` , `1..1` , `0..*` lub `1..*` ). Jeśli liczebność jest `0..*` lub `1..*` , wówczas wygenerowana właściwość reprezentuje kolekcję; w przeciwnym razie wygenerowana właściwość reprezentuje pojedynczy element modelu.|Zależy od typu relacji i tego, czy jest to rola źródłowa lub docelowa w relacji.|
|Nazwa|Nazwa roli domeny. Ta właściwość nie może zawierać odstępów.|Nazwa klasy domeny obiektu pełniącego rolę dla tej roli.|
|Propaguje kopię|`DoNotPropagateCopy` -Skopiowany obiekt pełniący rolę nie będzie miał kopii tego linku.<br /><br /> `PropagateCopyToLinkOnly` -Skopiowane łącze prowadzi do istniejącego przeciwległego obiektu pełniącego rolę.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer` -Skopiowane łącze wskazuje kopię przeciwległego obiektu pełniącego rolę.|`PropagateCopyToLinkAndOppositeRolePlayer` dla ról źródłowych osadzania.<br /><br /> `DoNotPropagateCopy` w przypadku innych ról.<br /><br /> Aby uzyskać więcej informacji, zobacz [Dostosowywanie zachowania kopiowania](../modeling/customizing-copy-behavior.md)|
|Propagowanie usuwania|`True` Aby usunąć element, który odgrywa tę rolę po usunięciu skojarzonego linku.|`True` dla obiektu docelowego roli osadzania.<br /><br /> `False` w przypadku innych ról.<br /><br /> Aby uzyskać więcej informacji, zobacz [Dostosowywanie zachowania usuwania](../modeling/customizing-deletion-behavior.md).|
|Nazwa właściwości|Nazwa właściwości wygenerowanej w kodzie obiektu pełniącego rolę. Ta nazwa nie może zawierać odstępów.|Nazwa przeciwległej roli, jeśli ta rola ma wartość zero-do-jednego lub liczebność jeden-do-jednego; w przeciwnym razie nazwa w liczbie mnogiej roli odwrotnej.|
|Obiekt pełniący rolę|Klasa domeny elementu, który może odtwarzać tę rolę w relacji. Ta właściwość jest tylko do odczytu.|Klasa domeny obiektu pełniącego rolę dla tej roli.|
|Uwagi|Nieformalne uwagi, które są skojarzone z rolą domeny.|\<none>|
|Kategoria|Kategoria, pod którą wygenerowana właściwość pojawia się w oknie **Właściwości** w wygenerowanym projektancie. Jeśli ta właściwość jest pusta, wygenerowana właściwość zostanie wyświetlona w obszarze Kategoria **różne**|\<none>|
|Opis|Opis używany do dokumentowania kodu i jest używany w interfejsie użytkownika wygenerowanego projektanta.<br /><br /> Opis jest wyświetlany w etykietce narzędzia IntelliSense dla wygenerowanej właściwości klasy obiektu pełniącego rolę.|`Description for`*pełna nazwa roli*|
|Nazwa wyświetlana|Nazwa wyświetlana w wygenerowanym projektancie dla roli domeny.|Skorygowana wartość właściwości Nazwa.|
|Słowo kluczowe pomocy|Opcjonalne słowo kluczowe, które jest używane do indeksowania pomocy klawisza F1 dla roli domeny.|\<none>|
|Nazwa wyświetlana właściwości|Nazwa wyświetlana w wygenerowanym projektancie dla wygenerowanej właściwości roli.|Wartość skorygowana właściwości Nazwa właściwości.|

> [!NOTE]
> Wartość domyślna nazwy wyświetlanej jest oparta na wartości skojarzonej właściwości przez Wstawianie spacji przed każdym wielkie litery, które jest poprzedzone znakiem małych liter i nie następuje po nim kolejnego znaku Case.

## <a name="see-also"></a>Zobacz też
 [Właściwości relacji domeny](../modeling/properties-of-domain-relationships.md)
