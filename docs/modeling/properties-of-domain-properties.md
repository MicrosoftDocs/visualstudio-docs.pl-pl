---
title: Właściwości właściwości domeny
description: Dowiedz się, jak właściwość domeny jest funkcją elementu modelu, który może przechowywać wartość, oraz jak właściwości domeny są wyświetlane w polu klasy domeny na diagramie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain properties
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f2f026f62c5440b48b04d05e080515c47dd11979
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390649"
---
# <a name="properties-of-domain-properties"></a>Właściwości właściwości domeny
Właściwość *domeny jest* funkcją elementu modelu, który może przechowywać wartość. Na przykład klasa `Person` domeny może mieć właściwości i `Name` `BirthDate` . W definicji DSL właściwości domeny są wymienione w polu klasy domeny na diagramie i w obszarze klasy domeny w Eksploratorze DSL. Aby uzyskać więcej informacji, [zobacz How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md).

> [!NOTE]
> Wyraz "property" ma dwa zastosowania. Właściwość *domeny to* funkcja zdefiniowana w klasie domeny. Z kolei wiele elementów DSL ma *właściwości*, które są wyświetlane w oknie **Właściwości** w definicji DSL. Na przykład każda właściwość domeny ma zestaw właściwości, które są opisane w tym temacie.

 W czasie uruchamiania, gdy użytkownik tworzy wystąpienia klasy domeny, wartości właściwości domeny są widoczne w oknie okno Właściwości i mogą być wyświetlane na kształtach.

 Większość właściwości domeny jest implementowane jako zwykłe właściwości CLR. Jednak z punktu widzenia programowania właściwości domeny mają bogatszą funkcjonalność niż zwykłe właściwości programu:

- Można zdefiniować reguły i zdarzenia, które monitorują stan właściwości. Aby uzyskać więcej informacji, zobacz [Odpowiadanie na zmiany i propagowanie ich.](../modeling/responding-to-and-propagating-changes.md)

- Transakcje pomagają zapobiegać niespójnym stanom. Aby uzyskać więcej informacji, zobacz [Nawigowanie po modelu i aktualizowanie go w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

  Po wybraniu właściwości domeny na diagramie lub w Eksploratorze DSL można zobaczyć następujące elementy w okno Właściwości. Aby uzyskać więcej informacji na temat używania tych elementów, zobacz Dostosowywanie i [rozszerzanie Domain-Specific języku](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Właściwość|Opis|Wartość domyślna|
|-|-|-|
|**Opis**|Opis używany do dokumentować interfejs użytkownika wygenerowanego projektanta.|\<none>|
|**Nazwa wyświetlana**|Nazwa, która będzie wyświetlana w wygenerowanym projektancie dla tej właściwości domeny. Może zawierać spacje i znaki interpunktowe, na przykład "Tytuł utworu".|\<none>|
|**Dostawca nazw elementów**|Ma to zastosowanie tylko wtedy, gdy ustawiono `Is Element Name` wartość `true` . Można napisać kod, który zawiera nazwę dla nowego elementu klasy domeny, przesłaniając zachowanie domyślne.<br /><br /> W pliku kodu w projekcie DSL utwórz klasę pochodzącą od klasy <xref:Microsoft.VisualStudio.Modeling.ElementNameProvider> .<br /><br /> Następnie w Eksploratorze DSL kliknij prawym przyciskiem myszy katalog główny DSL i kliknij polecenie Dodaj typ zewnętrzny. Wprowadź nazwę klasy.<br /><br /> Wybierz ponownie tę właściwość domeny, a następnie wybierz nazwę klasy z listy rozwijanej.|\<none>|
|**Modyfikator dostępu getter**|Poziom dostępu klasy domeny ( `public` lub `internal` ). Kontroluje to zakres, w którym kod programu może uzyskać dostęp do właściwości .|`public`|
|**Słowo kluczowe pomocy**|Opcjonalne słowo kluczowe używane do indeksowania pomocy F1 dla tej właściwości domeny.|\<none>|
|**Można przeglądać**|Jeśli `True` , właściwość domeny jest wyświetlana użytkownikowi w oknie właściwości, gdy modele tego DSL są otwarte.<br /><br /> Jeśli `False` , właściwość domeny jest ukryta w interfejsie użytkownika.<br /><br /> Jeśli chcesz, aby właściwość domeny była widoczna, ale tylko do odczytu, ustaw właściwość Jest tylko **do odczytu interfejsu użytkownika.**|`True`|
|**Is, nazwa elementu**|Jeśli , ta właściwość domeny będzie wyświetlana jako nazwa jej `True` elementu modelu w Eksploratorze DSL.<br /><br /> Nowe elementy modelu otrzymają unikatową wartość domyślną dla tej właściwości. Jeśli chcesz kontrolować sposób generowania tych wartości, ustaw **dostawcę nazw elementów**.|`False`|
|**Jest tylko do odczytu interfejsu użytkownika**|Jeśli `True` wartość właściwości domeny nie może zostać zmieniona przy użyciu interfejsu użytkownika. Nadal można go ustawić za pomocą programów i będzie widoczny w okno Właściwości.<br /><br /> Jeśli chcesz ukryć właściwość domeny przed użytkownikiem, ustaw właściwość **Jest przeglądanie.** Jeśli chcesz kontrolować dostęp za pomocą programów, ustaw **modyfikator dostępu ustawiającego**.|`False`|
|**Rodzaj**|Rodzaj właściwości domeny ( `Normal` `Calculated` , lub `CustomStorage` ). Aby uzyskać więcej informacji, zobacz [Właściwości magazynu obliczeniowego i niestandardowego.](../modeling/calculated-and-custom-storage-properties.md)|`Normal`|
|**Nazwa**|Nazwa tej właściwości domeny. Musi to być prawidłowy identyfikator, na przykład **SongTitle**.|\<none>|
|**Uwagi**|Uwagi nieformalne skojarzone z tą właściwością domeny.|\<none>|
|**Modyfikator dostępu ustawiającego**|Modyfikator dostępu dla ustawiającego. Kontroluje to zakres, w którym kod programu może ustawić właściwość .|`public`|
|**Typ**|Typ właściwości. Aby dodać do listy dostępnych typów, kliknij prawym przyciskiem myszy katalog główny DSL w eksploratorze DSL, a następnie kliknij polecenie **Dodaj typ zewnętrzny.**|`String`|

## <a name="see-also"></a>Zobacz też

- [narzędzia języka specyficznego dla domeny słownik](/previous-versions/bb126564(v=vs.100))