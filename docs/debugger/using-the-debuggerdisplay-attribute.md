---
title: Korzystanie z atrybutu DebuggerDisplay | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 83a5304da009aa35eefb91f064929a58444f139f
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56317006"
---
# <a name="using-the-debuggerdisplay-attribute-c-visual-basic-f-ccli"></a>Korzystanie z atrybutu DebuggerDisplay (C#, Visual Basic F#, C + +/ CLI)
<xref:System.Diagnostics.DebuggerDisplayAttribute> Kontroluje sposób wyświetlania obiektu, właściwość lub pole w oknach zmiennych debugera. Ten atrybut może dotyczyć typy delegatów, właściwości, pola i zestawy.

`DebuggerDisplay` Atrybut ma jeden argument, czyli ciąg tekstowy, który ma być wyświetlana w kolumnie wartość dla wystąpienia typu. Ten ciąg może zawierać nawiasy klamrowe (`{` i `}`). Tekst w parę nawiasów klamrowych jest oceniane jako pola, właściwości lub metody.

Jeśli klasa ma zastąpione `ToString()` metoda, debuger używa przeciążonej zamiast domyślnego `{<typeName>}`. W związku z tym jeśli zastępowano `ToString()` metoda, debuger używa przeciążonej zamiast domyślnego`{<typeName>}`, i nie trzeba używać `DebuggerDisplay`. Jeśli używasz zarówno `DebuggerDisplay` atrybut ma pierwszeństwo przed zastąpione `ToString()` metody.

Czy tym niejawne ocenia debuger `ToString()` wywołanie zależy od ustawień użytkownika w **narzędzia / Opcje / Debugowanie** okno dialogowe. Visual Basic nie implementuje tym niejawne `ToString()` oceny.

> [!IMPORTANT]
> Jeśli **pokazywanie nieprzetworzonej struktury obiektów w oknach zmiennych** zaznaczono pole wyboru w **narzędzia/Opcje / Debugowanie** okno dialogowe, a następnie `DebuggerDisplay` atrybut jest ignorowany.

> [!NOTE]
> Dla kodu natywnego, atrybut ten jest obsługiwany tylko w języku C + +/ CLI, kod.

W poniższej tabeli przedstawiono niektóre możliwości wykorzystania `DebuggerDisplay` atrybutu i przykładowe dane wyjściowe.

|Atrybut|Dane wyjściowe znajdujących się w kolumnie wartości|
|---------------| - |
|`[DebuggerDisplay("x = {x} y = {y}")]`<br /><br /> Używane w danym typie z polami `x` i `y`.|`x = 5 y = 18`|
|`[DebuggerDisplay("String value is {getString()}")]`Składnia parametru może się różnić między językami. W związku z tym jej używać z rozwagą.|`String value is [5, 6, 6]`|

`DebuggerDisplay` Ponadto można zaakceptować nazwanych parametrów.

|Parametry|Cel|
|----------------|-------------|
|`Name`, `Type`|Parametry te mają wpływ na **nazwa** i **typu** kolumn w oknach zmiennych. (One może być równa ciągów za pomocą tej samej składni jako Konstruktor.) Nadużywanie tych parametrów lub korzystanie z nich nieprawidłowo, może spowodować mylące danych wyjściowych.|
|`Target`, `TargetTypeName`|Określa typ docelowy, gdy ten atrybut jest używany na poziomie zestawu.|

Plik autoexp.cs używa atrybutu DebuggerDisplay na poziomie zestawu. Plik autoexp.cs Określa rozszerzenia domyślne używane przez program Visual Studio dla obiektów platformy .NET. Można przejrzeć plik autoexp.cs przykładów dotyczących sposobów używania atrybutu DebuggerDisplay lub można modyfikować i skompiluj plik autoexp.cs, aby zmienić domyślne rozszerzenia. Pamiętaj utworzyć kopię zapasową pliku autoexp.cs, przed przystąpieniem do modyfikacji.

Aby skompilować autoexp.cs, otwórz się wiersz polecenia dla deweloperów dla VS2015 i uruchom następujące polecenia

```cmd
cd <directory containing autoexp.cs>
csc /t:library autoexp.cs
```

Zmiany autoexp.dll będą pobierane w następnej sesji debugowania.

## <a name="using-expressions-in-debuggerdisplay"></a>Używanie wyrażeń w DebuggerDisplay
Mimo że można użyć wyrażenia ogólnych między nawiasami klamrowymi w atrybutu DebuggerDisplay, to rozwiązanie nie jest zalecane.

Ogólne wyrażenia w DebuggerDisplay ma niejawne dostęp do `this` wskaźnik dla bieżącego wystąpienia na typ docelowy. Wyrażenie nie ma dostępu do aliasów, zmienne lokalne lub wskaźników. Jeśli wyrażenie odwołuje się do właściwości, atrybutów na te właściwości nie są przetwarzane. Na przykład C# kodu `[DebuggerDisplay("Object {count - 2}")]` zostanie wyświetlony `Object 6` Jeśli pole `count` został 8.

Używanie wyrażeń w DebuggerDisplay może prowadzić do następujących problemów:

- Ocenianie wyrażenia jest najbardziej kosztownych operacji w debugerze i wyrażenie jest obliczane na każdym razem, gdy jest on wyświetlany. Może to spowodować problemy z wydajnością w krokowe wykonywanie kodu. Na przykład wyrażenie złożone, który służy do wyświetlania wartości w kolekcji lub na liście może być bardzo wolno po dużą liczbę elementów.

- Wyrażenia są obliczane przez ewaluatora wyrażeń języka bieżącej ramki stosu a nie przez ewaluatora języka, w którym został zapisany wyrażenia. Może to spowodować nieprzewidywalne skutki, gdy języki są różne.

- Obliczenia wyrażenia można zmienić stanu aplikacji. Na przykład wyrażenie, które ustawia wartości właściwości mutuje wartość właściwości wykonywanie kodu.

  Jednym ze sposobów, aby ograniczyć możliwe problemy obliczania wyrażenia jest utworzenie właściwości prywatnej, który wykonuje operację i zwraca ciąg. Atrybut DebuggerDisplay następnie wyświetlić wartość tej właściwości prywatnej. Poniższy przykład implementuje tego wzorca:

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
", Nq" sufiks informuje ewaluatora wyrażenia, aby usunąć znaki cudzysłowu, podczas wyświetlania wartości końcowej (nq = nie cudzysłowów).

## <a name="example"></a>Przykład
Poniższy przykład kodu pokazuje sposób użycia `DebuggerDisplay`, wraz z `DebuggerBrowseable` i `DebuggerTypeProxy`. Podczas wyświetlania w oknie zmiennych debugera, takie jak **Obejrzyj** oknie tworzy ekspansja, która wygląda w następujący sposób:

|**Nazwa**|**Wartość**|**Typ**|
|--------------|---------------|--------------|
|Key|"trzy"|Obiekt {ciąg}|
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

    private string DebuggerDisplay { get { return "Count = " + hashtable.Count); } }

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
[Korzystanie z atrybutu DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md)  
[Tworzenie niestandardowych widoków obiektów zarządzanych](../debugger/create-custom-views-of-dot-managed-objects.md)  
[Specyfikatory formatu w języku C#](../debugger/format-specifiers-in-csharp.md)  
[Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)
