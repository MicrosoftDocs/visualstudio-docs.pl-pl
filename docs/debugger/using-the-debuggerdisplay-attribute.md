---
title: Wyświetlanie informacji niestandardowych za pomocą DebuggerDisplay | Microsoft Docs
ms.date: 01/09/2019
ms.topic: conceptual
helpviewer_keywords:
- attributes, debugger
- DebuggerDisplay attribute
- DebuggerDisplayAttribute class
ms.assetid: f4eb7c76-af4e-493b-9ab6-9cb05949d9b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 866ad705f16e9eabb097e9c0c9064d2c379ebf9f
ms.sourcegitcommit: 1507baf3a336bbb6511d4c3ce73653674831501b
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72349621"
---
# <a name="tell-the-debugger-what-to-show-using-the-debuggerdisplay-attribute-c-visual-basic-f-ccli"></a>Określ debuger, który ma być wyświetlany przy użyciu atrybutu DebuggerDisplayC#(, Visual Basic F#, C++,/CLI)

@No__t_0 kontroluje sposób wyświetlania obiektu, właściwości lub pola w oknach zmiennych debugera. Ten atrybut może być stosowany do typów, delegatów, właściwości, pól i zestawów. W przypadku zastosowania do typu podstawowego atrybut ma zastosowanie również do podklasy.

Atrybut `DebuggerDisplay` ma jeden argument, który jest ciągiem, który ma być wyświetlany w kolumnie value dla wystąpień typu. Ten ciąg może zawierać nawiasy klamrowe (`{` i `}`). Tekst w parze nawiasów klamrowych jest obliczany jako pole, właściwość lub metoda.

Jeśli klasa ma zastąpioną metodę `ToString()`, debuger używa zastąpionej metody zamiast domyślnej `{<typeName>}`. W takim przypadku w przypadku zastąpienia metody `ToString()` debuger używa zastąpionej metody zamiast domyślnej `{<typeName>}` i nie trzeba używać `DebuggerDisplay`. Jeśli używasz obu, atrybut `DebuggerDisplay` ma pierwszeństwo przed zastąpioną metodą `ToString()`. Atrybut `DebuggerDisplay` ma również pierwszeństwo przed zastąpioną metodą `ToString()` w podklasy.

Czy debuger szacuje to niejawne wywołanie `ToString()` zależy od ustawienia użytkownika w oknie dialogowym **Narzędzia/Opcje/debugowanie** . Visual Basic nie implementuje tej niejawnej `ToString()` oceny.

> [!IMPORTANT]
> Jeśli pole wyboru **Pokaż nieprzetworzoną strukturę obiektów w zmiennych oknach** jest zaznaczone w oknie dialogowym **Narzędzia/Options/debugowanie** , atrybut `DebuggerDisplay` jest ignorowany.

> [!NOTE]
> W przypadku kodu natywnego ten atrybut jest obsługiwany tylko C++w kodzie/CLI.

W poniższej tabeli przedstawiono niektóre możliwe zastosowania atrybutu `DebuggerDisplay` i przykładowych danych wyjściowych.

|Atrybut|Dane wyjściowe pojawiają się w kolumnie Value|
|---------------| - |
|`[DebuggerDisplay("x = {x} y = {y}")]`<br /><br /> Używane dla typu z polami `x` i `y`.|`x = 5 y = 18`|
|Składnia `[DebuggerDisplay("String value is {getString()}")]`Parameter może się różnić w różnych językach. Z tego względu należy z nich korzystać.|`String value is [5, 6, 6]`|

`DebuggerDisplay` może również akceptować nazwane parametry.

|Parametry|Cel|
|----------------|-------------|
|`Name`, `Type`|Te parametry mają wpływ na kolumny **nazw** i **typów** zmiennych okien. (Mogą być ustawiane na ciągi przy użyciu tej samej składni co Konstruktor). Użycie tych parametrów lub nieprawidłowe użycie ich może spowodować mylące wyprowadzanie danych wyjściowych.|
|`Target`, `TargetTypeName`|Określa typ docelowy, gdy atrybut jest używany na poziomie zestawu.|

Plik autoexp.cs używa atrybutu DebuggerDisplay na poziomie zestawu. Plik autoexp.cs określa domyślne rozszerzenia, które program Visual Studio używa dla obiektów .NET. Można przejrzeć plik autoexp.cs, aby poznać przykłady użycia atrybutu DebuggerDisplay lub zmodyfikować i skompilować plik autoexp.cs, aby zmienić domyślne rozszerzenia. Przed przystąpieniem do modyfikacji należy wykonać kopię zapasową pliku autoexp.cs.

Aby skompilować autoexp.cs, Otwórz wiersz polecenia dla deweloperów dla programu VS2015 i uruchom następujące polecenia

```cmd
cd <directory containing autoexp.cs>
csc /t:library autoexp.cs
```

Zmiany w autoexp. dll zostaną pobrane w następnej sesji debugowania.

## <a name="using-expressions-in-debuggerdisplay"></a>Używanie wyrażeń w DebuggerDisplay
Chociaż można użyć wyrażenia ogólnego między nawiasami klamrowymi w atrybucie DebuggerDisplay, ta metoda nie jest zalecana.

Wyrażenie ogólne w DebuggerDisplay ma niejawny dostęp do wskaźnika `this` tylko dla bieżącego wystąpienia typu docelowego. Wyrażenie nie ma dostępu do aliasów, zmiennych lokalnych ani wskaźników. Jeśli wyrażenie odwołuje się do właściwości, atrybuty tych właściwości nie są przetwarzane. Na przykład C# kod `[DebuggerDisplay("Object {count - 2}")]` będzie wyświetlany `Object 6`, jeśli pole `count` miało wartość 8.

Używanie wyrażeń w DebuggerDisplay może prowadzić do następujących problemów:

- Ocenianie wyrażeń jest najtańszą operacją w debugerze, a wyrażenie jest oceniane za każdym razem, gdy jest wyświetlany. Może to spowodować problemy z wydajnością podczas stopniowego wykonywania kodu. Na przykład złożone wyrażenie, które jest używane do wyświetlania wartości w kolekcji lub listy, może być bardzo wolne, gdy liczba elementów jest duża.

- Wyrażenia są oceniane przez ewaluatora wyrażeń w języku bieżącej ramki stosu, a nie przez ewaluatora języka, w którym zapisano wyrażenie. Może to spowodować nieprzewidywalne wyniki, gdy języki są różne.

- Obliczenie wyrażenia może zmienić stan aplikacji. Na przykład wyrażenie ustawiające wartość właściwości jest mutacją wartości właściwości w wykonywanym kodzie.

  Jednym ze sposobów zmniejszenia możliwych problemów dotyczących oceny wyrażeń jest utworzenie prywatnej właściwości, która wykonuje operację i zwraca ciąg. Atrybut DebuggerDisplay może następnie wyświetlić wartość tej właściwości prywatnej. Poniższy przykład implementuje ten wzorzec:

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

Sufiks ", NQ" informuje ewaluatora wyrażeń, aby usunąć cudzysłowy podczas wyświetlania końcowej wartości (NQ = brak cudzysłowów).

## <a name="example"></a>Przykład
Poniższy przykład kodu pokazuje, jak używać `DebuggerDisplay` wraz z `DebuggerBrowseable` i `DebuggerTypeProxy`. Gdy wyświetlane w oknie zmiennych debugera, takie jak okno **czujki** , tworzy rozszerzenie, które wygląda następująco:

|**Nazwa**|**Wartość**|**Wprowadź**|
|--------------|---------------|--------------|
|Key|trzecim|obiekt {String}|
|Wartość|3|Obiekt {int}|

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
- [Tworzenie niestandardowych widoków obiektów zarządzanych](../debugger/create-custom-views-of-dot-managed-objects.md)
- [Specyfikatory formatu w języku C#](../debugger/format-specifiers-in-csharp.md)
- [Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
