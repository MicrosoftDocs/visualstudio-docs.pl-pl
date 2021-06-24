---
title: Wyświetlanie niestandardowych informacji przy użyciu debugerawyświetlać | Microsoft Docs
description: Użyj wystąpienia DebuggerDisplayAttribute, aby kontrolować sposób wyświetlania obiektu, właściwości lub pola w oknach zmiennych debugera.
ms.custom: SEO-VS-2020
ms.date: 01/09/2019
ms.topic: how-to
helpviewer_keywords:
- attributes, debugger
- DebuggerDisplay attribute
- DebuggerDisplayAttribute class
ms.assetid: f4eb7c76-af4e-493b-9ab6-9cb05949d9b3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e9579e4969cb53ed2f1bcf749e8114386af85d0
ms.sourcegitcommit: 674d3fafa7c9e0cb0d1338027ef419a49c028c36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2021
ms.locfileid: "112602145"
---
# <a name="tell-the-debugger-what-to-show-using-the-debuggerdisplay-attribute-c-visual-basic-f-ccli"></a>Poinformuj debuger, co pokazać przy użyciu atrybutu DebuggerDisplay (C#, Visual Basic, F#, C++/CLI)

Kontrolka <xref:System.Diagnostics.DebuggerDisplayAttribute> określa sposób wyświetlania obiektu, właściwości lub pola w oknach zmiennych debugera. Ten atrybut można stosować do typów, delegatów, właściwości, pól i zestawów. W przypadku zastosowania do typu podstawowego atrybut ma również zastosowanie do podklasy.

Atrybut ma pojedynczy argument, który jest ciągiem, który ma być wyświetlany w kolumnie `DebuggerDisplay` wartości dla wystąpień typu. Ten ciąg może zawierać nawiasy klamrowe ( `{` i `}` ). Tekst w parze nawiasów klamrowych jest obliczany jako pole, właściwość lub metoda.

Jeśli klasa ma metodę przesłoniętą, debuger używa `ToString()` metody overridden zamiast domyślnej `{<typeName>}` metody . W związku z tym, jeśli metoda została przesłonięta, debuger używa metody overridden zamiast domyślnej metody i nie `ToString()` `{<typeName>}` trzeba używać metody `DebuggerDisplay` . Jeśli używasz obu, `DebuggerDisplay` atrybut ma pierwszeństwo przed przesłoniętą `ToString()` metodą. Atrybut `DebuggerDisplay` ma również pierwszeństwo przed przesłoniętą metodą w `ToString()` podklasie.

To, czy debuger ocenia to niejawne wywołanie, zależy od ustawienia użytkownika w oknie dialogowym `ToString()` Narzędzia / Opcje / **Debugowanie.**

> [!IMPORTANT]
> Jeśli Pokaż **nieprzetworzone struktury** obiektów w zmiennych okna pole wyboru jest zaznaczone w Narzędzia **/ Opcje / Debugowanie** okno dialogowe, a następnie atrybut `DebuggerDisplay` jest ignorowany.

> [!NOTE]
> W przypadku kodu natywnego ten atrybut jest obsługiwany tylko w kodzie C++/CLI.

W poniższej tabeli przedstawiono niektóre możliwe zastosowania `DebuggerDisplay` atrybutu i przykładowe dane wyjściowe.

|Atrybut|Dane wyjściowe wyświetlane w kolumnie Wartość|
|---------------| - |
|`[DebuggerDisplay("x = {x} y = {y}")]`<br /><br /> Używany w typie z polami `x` i `y` .|`x = 5 y = 18`|
|`[DebuggerDisplay("String value is {getString()}")]`Składnia parametrów może się różnić w zależności od języka. Dlatego należy używać go ostrożnie.|`String value is [5, 6, 6]`|

`DebuggerDisplay` Może również akceptować nazwane parametry.

|Parametry|Przeznaczenie|
|----------------|-------------|
|`Name`, `Type`|Te parametry mają wpływ **na kolumny** **Name i Type** okien zmiennych. (Można je ustawić na ciągi przy użyciu tej samej składni co konstruktor). Użycie tych parametrów lub ich nieprawidłowe użycie może spowodować mylące dane wyjściowe.|
|`Target`, `TargetTypeName`|Określa typ docelowy, gdy atrybut jest używany na poziomie zestawu.|

Plik autoexp.cs używa atrybutu DebuggerDisplay na poziomie zestawu. Plik autoexp.cs określa domyślne rozszerzenia używane Visual Studio dla obiektów .NET. Możesz przeanalizować plik autoexp.cs, aby uzyskać przykłady użycia atrybutu DebuggerDisplay, lub zmodyfikować i skompilować plik autoexp.cs, aby zmienić domyślne rozszerzenia. Pamiętaj o kopii zapasowej pliku autoexp.cs przed jego zmodyfikowaniem.

Aby skompilować autoexp.cs, otwórz wiersz polecenia dla deweloperów dla programu VS2015 i uruchom następujące polecenia

```cmd
cd <directory containing autoexp.cs>
csc /t:library autoexp.cs
```

Zmiany w autoexp.dll zostaną wprowadzone w następnej sesji debugowania.

## <a name="using-expressions-in-debuggerdisplay"></a>Używanie wyrażeń w debugerzeDisplay
Chociaż można użyć ogólnego wyrażenia między nawiasami klamrowych w atrybutze DebuggerDisplay, to rozwiązanie nie jest zalecane.

Wyrażenie ogólne w debugerze DebuggerDisplay ma niejawny dostęp do wskaźnika tylko dla bieżącego wystąpienia `this` typu docelowego. Wyrażenie nie ma dostępu do aliasów, lokalizacji lokalnych ani wskaźników. Jeśli wyrażenie odwołuje się do właściwości, atrybuty tych właściwości nie są przetwarzane. Na przykład kod w języku C# `[DebuggerDisplay("Object {count - 2}")]` będzie `Object 6` wyświetlany, jeśli pole `count` miało wartość 8.

Używanie wyrażeń w debugerze DebuggerDisplay może prowadzić do następujących problemów:

- Ocenianie wyrażeń jest najdroższą operacją w debugerze, a wyrażenie jest oceniane za każdym razem, gdy jest wyświetlane. Może to spowodować problemy z wydajnością wykonywania krokowego kodu. Na przykład złożone wyrażenie, które jest używane do wyświetlania wartości w kolekcji lub na liście, może być bardzo powolne, gdy liczba elementów jest duża.

- Wyrażenia są oceniane przez ewaluator wyrażeń języka bieżącej ramki stosu, a nie przez ewaluator języka, w którym wyrażenie zostało napisane. Może to spowodować nieprzewidywalne wyniki, gdy języki są różne.

- Ocenianie wyrażenia może zmienić stan aplikacji. Na przykład wyrażenie, które ustawia wartość właściwości, mutuje wartość właściwości w wykonywanym kodzie.

  Jednym ze sposobów zmniejszenia możliwych problemów z oceną wyrażeń jest utworzenie właściwości prywatnej, która wykonuje operację i zwraca ciąg. Atrybut DebuggerDisplay może następnie wyświetlać wartość tej właściwości prywatnej. W poniższym przykładzie zaimplementowano ten wzorzec:

```csharp
[DebuggerDisplay("{DebuggerDisplay,nq}")]
public sealed class MyClass
{
    public int count { get; set; }
    public bool flag { get; set; }
    private string DebuggerDisplay
    {
        get
        {
            return string.Format("Object {0}", count - 2);
        }
    }
}
```

Sufiks ",nq" nakazuje ewaluatorowi wyrażeń usunięcie cudzysłowów podczas wyświetlania wartości końcowej (nq = brak cudzysłowów).

## <a name="example"></a>Przykład
Poniższy przykład kodu pokazuje, jak używać funkcji `DebuggerDisplay` wraz z i `DebuggerBrowsable` `DebuggerTypeProxy` . W przypadku wyświetlania w oknie zmiennych debugera, takim jak okno **Czujka,** tworzy rozszerzenie, które wygląda następująco:

|**Nazwa**|**Wartość**|**Typ**|
|--------------|---------------|--------------|
|Klucz|"trzy"|obiekt {string}|
|Wartość|3|obiekt {int}|

```csharp
[DebuggerDisplay("{value}", Name = "{key}")]
internal class KeyValuePairs
{
    private IDictionary dictionary;
    private object key;
    private object value;
    public KeyValuePairs(IDictionary dictionary, object key, object value)
    {
        this.value = value;
        this.key = key;
        this.dictionary = dictionary;
    }

    public object Key
    {
        get { return key; }
        set
        {
            object tempValue = dictionary[key];
            dictionary.Remove(key);
            key = value;
            dictionary.Add(key, tempValue);
        }
    }

    public object Value
    {
        get { return this.value; }
        set
        {
            this.value = value;
            dictionary[key] = this.value;
        }
    }
}

[DebuggerDisplay("{DebuggerDisplay,nq}")]
[DebuggerTypeProxy(typeof(HashtableDebugView))]
class MyHashtable
{
    public Hashtable hashtable;

    public MyHashtable()
    {
        hashtable = new Hashtable();
    }

    private string DebuggerDisplay { get { return "Count = " + hashtable.Count; } }

    private class HashtableDebugView
    {
        private MyHashtable myhashtable;
        public HashtableDebugView(MyHashtable myhashtable)
        {
            this.myhashtable = myhashtable;
        }

        [DebuggerBrowsable(DebuggerBrowsableState.RootHidden)]
        public KeyValuePairs[] Keys
        {
            get
            {
                KeyValuePairs[] keys = new KeyValuePairs[myhashtable.hashtable.Count];

                int i = 0;
                foreach (object key in myhashtable.hashtable.Keys)
                {
                    keys[i] = new KeyValuePairs(myhashtable.hashtable, key, myhashtable.hashtable[key]);
                    i++;
                }
                return keys;
            }
        }
    }
}
```

## <a name="see-also"></a>Zobacz też

- [Korzystanie z atrybutu DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)
- [Tworzenie niestandardowych widoków obiektów zarządzanych](../debugger/create-custom-views-of-managed-objects.md)
- [Specyfikatory formatu w języku C#](../debugger/format-specifiers-in-csharp.md)
- [Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
