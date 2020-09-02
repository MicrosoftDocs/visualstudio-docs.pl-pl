---
title: Przy użyciu atrybutu DebuggerDisplay | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- attributes [C#], debugger
- DebuggerDisplay attribute
- DebuggerDisplayAttribute class
ms.assetid: f4eb7c76-af4e-493b-9ab6-9cb05949d9b3
caps.latest.revision: 50
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aba6feb17a4e7bd4cabfe40bd45480a0f7a9f552
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683934"
---
# <a name="using-the-debuggerdisplay-attribute"></a>Używanie atrybutu DebuggerDisplay
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:System.Diagnostics.DebuggerDisplayAttribute>Kontroluje sposób wyświetlania obiektu, właściwości lub pola w zmiennych debugera systemu Windows. Ten atrybut może być stosowany do typów, delegatów, właściwości, pól i zestawów.  
  
 `DebuggerDisplay`Atrybut ma jeden argument, który jest ciągiem, który ma być wyświetlany w kolumnie wartość dla wystąpień typu. Ten ciąg może zawierać nawiasy klamrowe ( `{` i `}` ). Tekst w parze nawiasów klamrowych jest obliczany jako pole, właściwość lub metoda.  
  
 Jeśli klasa ma przesłoniętą `ToString()` metodę, debuger używa zastąpionej metody zamiast wartości domyślnej `{<typeName>}` . W takim przypadku w przypadku zastąpienia `ToString()` metody debuger używa zastąpionej metody zamiast wartości domyślnej `{<typeName>}` i nie trzeba używać `DebuggerDisplay` . Jeśli używasz obu, `DebuggerDisplay` atrybut ma pierwszeństwo przed zastąpioną `ToString()` metodą.  
  
 Czy debuger szacuje to niejawne `ToString()` wywołanie zależnie od ustawienia użytkownika w oknie dialogowym **Narzędzia/Opcje/debugowanie** . Visual Basic nie implementuje tej niejawnej `ToString()` oceny.  
  
> [!IMPORTANT]
> Jeśli pole wyboru **Pokaż nieprzetworzoną strukturę obiektów w zmiennych oknach** jest zaznaczone w oknie dialogowym **Narzędzia/Options/debugowanie** , `DebuggerDisplay` atrybut jest ignorowany.  
  
 W poniższej tabeli przedstawiono niektóre możliwe zastosowania `DebuggerDisplay` atrybutu i przykładowych danych wyjściowych.  
  
|Atrybut|Dane wyjściowe pojawiają się w kolumnie **Value** )|  
|---------------|------------------------------------------------|  
|`[DebuggerDisplay("x = {x} y = {y}")]`<br /><br /> Używane dla typu z polami `x` i `y` .|`x = 5 y = 18`|  
|`[DebuggerDisplay("String value is {getString()}")]`Składnia parametru może się różnić w różnych językach. Z tego względu należy z nich korzystać.|`String value is [5, 6, 6]`|  
  
 `DebuggerDisplay` może również akceptować nazwane parametry.  
  
|Parametry|Przeznaczenie|  
|----------------|-------------|  
|`Name`, `Type`|Te parametry mają wpływ na kolumny **nazw** i **typów** zmiennych okien. (Mogą być ustawiane na ciągi przy użyciu tej samej składni co Konstruktor). Użycie tych parametrów lub nieprawidłowe użycie ich może spowodować mylące wyprowadzanie danych wyjściowych.|  
|`Target`, `TargetTypeName`|Określa typ docelowy, gdy atrybut jest używany na poziomie zestawu.|  
  
 Plik autoexp.cs używa atrybutu DebuggerDisplay na poziomie zestawu. Plik autoexp.cs określa domyślne rozszerzenia, które program Visual Studio używa dla obiektów .NET. Można przejrzeć plik autoexp.cs, aby poznać przykłady użycia atrybutu DebuggerDisplay lub zmodyfikować i skompilować plik autoexp.cs, aby zmienić domyślne rozszerzenia. Przed przystąpieniem do modyfikacji należy wykonać kopię zapasową pliku autoexp.cs.  
  
 Aby skompilować autoexp.cs, Otwórz wiersz polecenia dla deweloperów dla programu VS2015 i uruchom następujące polecenia  
  
```  
cd <directory containing autoexp.cs>  
csc /t:library autoexp.cs  
```  
  
 Zmiany w autoexp.dll zostaną pobrane w następnej sesji debugowania.  
  
## <a name="using-expressions-in-debuggerdisplay"></a>Używanie wyrażeń w DebuggerDisplay  
 Chociaż można użyć wyrażenia ogólnego między nawiasami klamrowymi w atrybucie DebuggerDisplay, ta metoda nie jest zalecana.  
  
 Wyrażenie ogólne w DebuggerDisplay ma niejawny dostęp do `this` wskaźnika dla bieżącego wystąpienia tylko typu docelowego. Wyrażenie nie ma dostępu do aliasów, zmiennych lokalnych ani wskaźników. Jeśli wyrażenie odwołuje się do właściwości, atrybuty tych właściwości nie są przetwarzane. Na przykład kod C# `[DebuggerDisplay("Object {count - 2}"`  będzie wyświetlany, `Object 6` Jeśli pole `count` miało wartość 8.  
  
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
             return string.Format("("Object {0}", count - 2);  
        }      
    }  
}  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak używać `DebuggerDisplay` razem z `DebuggerBrowseable` i `DebuggerTypeProxy` . Gdy wyświetlane w oknie zmiennych debugera, takie jak okno **czujki** , tworzy rozszerzenie, które wygląda następująco:  
  
|**Nazwa**|**Wartość**|**Typ**|  
|--------------|---------------|--------------|  
|Klucz|trzecim|obiekt {String}|  
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
    }    private string DebuggerDisplay    {        get { return "Count = " + hashtable.Count); }    }  
  
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
 [Używanie debugowania atrybutów DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md) [z atrybutami wyświetlania debugera](https://msdn.microsoft.com/library/72bb7aa9-459b-42c4-9163-9312fab4c410)
