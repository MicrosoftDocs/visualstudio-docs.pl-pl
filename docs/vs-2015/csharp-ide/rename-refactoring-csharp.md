---
title: Refaktoryzacja zmiany nazwy (C#) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Rename
- Rename refactoring [C#]
ms.assetid: 268942fc-b142-4dfa-8d90-bedd548c2e4f
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 971ca4e94f28016335483a03f4b0121de587f00d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439954"
---
# <a name="rename-refactoring-c"></a>Refaktoryzacja zmiany nazwy (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Zmień nazwę** jest funkcją refaktoryzacji w programie Visual Studio zintegrowane środowisko programistyczne (IDE), która zapewnia łatwy sposób można zmienić nazwy identyfikatorów dla kodu symbole, takie jak pola, zmienne lokalne, metody, przestrzenie nazw, właściwości i typów. **Zmień nazwę** może służyć do zmiany nazwy w komentarzach, a także w ciągach oraz zmienić deklaracje i wywołania identyfikatora.  
  
> [!NOTE]
> Korzystając z kontroli źródła dla programu Visual Studio, Pobierz najnowszą wersję źródła, przed podjęciem próby wykonania Refaktoryzacja zmiany nazwy.  
  
 Refaktoryzacja zmiany nazwy jest dostępna w następujących funkcji programu Visual Studio:  
  
|Funkcja|Zachowanie refaktoryzacji w środowisku IDE|  
|-------------|----------------------------------------|  
|Edytor kodu|Refaktoryzacja zmiany nazwy jest dostępna w edytorze kodu, gdy umieść kursor na niektórych rodzajów kodu symboli. Gdy kursor znajduje się w tym miejscu, można wywołać **Zmień nazwę** polecenia, wpisując skrót (CTRL + R, CTRL + R) lub wybierając **Zmień nazwę** polecenia tagu inteligentnego, w menu skrótów lub  **Refaktoryzuj** menu.|  
|Widok klas|Po wybraniu identyfikatora w widoku klas, Refaktoryzacja zmiany nazwy jest dostępne z menu skrótów i **Refaktoryzuj** menu.|  
|Przeglądarka obiektów|Po wybraniu identyfikatora w przeglądarce obiektów, Refaktoryzacja zmiany nazwy jest dostępna tylko z **Refaktoryzuj** menu.|  
|Siatki właściwości projektanta Windows Forms|W **siatki właściwości** programu Windows Forms Designer, zmiana nazwy kontrolki zostanie zainicjowana operacja zmiany nazwy dla tej kontrolki. **Zmień nazwę** nie pojawi się okno dialogowe.|  
|Eksplorator rozwiązań|W **Eksploratora rozwiązań**, **Zmień nazwę** polecenie jest dostępne w menu skrótów. Jeśli wybranym pliku źródłowym zawiera klasy, których nazwa klasy jest taka sama jak nazwa pliku, możesz użyć tego polecenia, jednocześnie Zmień nazwę pliku źródłowego i wykonywanie, Refaktoryzacja zmiany nazwy.<br /><br /> Na przykład jeśli utworzysz domyślnej aplikacji Windows, a następnie zmień nazwę Form1.cs TestForm.cs, nazwa pliku źródłowego Form1.cs zmieni się na TestForm.cs i class Form1 i wszystkie odwołania do czy klasa zmieni nazwę na TestForm. **Uwaga:**  **Cofnij** polecenie (CTRL + Z) tylko cofnąć Refaktoryzacja zmiany nazwy w kodzie i będzie nie zmieniać nazwy pliku z powrotem do oryginalnej nazwy. <br /><br /> Jeśli wybranym pliku źródłowym nie zawiera klasy, których nazwa jest taka sama jak nazwa pliku **Zmień nazwę** polecenia w pliku **Eksploratora rozwiązań** tylko zmienić nazwę pliku źródłowego i nie zostanie wykonany zmiany nazwy refaktoryzacji.|  
  
## <a name="rename-operations"></a>Zmień nazwę działania  
 Podczas wykonywania **Zmień nazwę**, aparat refaktoryzacji wykonuje określonej operacji zmiany nazwy dla każdego symbolu kodu, zgodnie z opisem w poniższej tabeli.  
  
|Kod symbolu|Operacji zmiany nazwy|  
|-----------------|----------------------|  
|Pole|Zmienia deklaracji i użycia pola na nową nazwę.|  
|Zmienna lokalna|Zmienia deklaracji i użycia zmiennej na nową nazwę.|  
|Metoda|Zmienia nazwę metody i wszystkie odwołania do tej metody na nową nazwę. **Uwaga:**  Po zmianie nazwy metody rozszerzenia operacji zmiany nazwy propaguje do wszystkich wystąpień metody, które znajdują się w zakresie, niezależnie od tego, czy metoda rozszerzenia jest używany jako metodę statyczną lub metodą wystąpienia. Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](http://msdn.microsoft.com/library/175ce3ff-9bbf-4e64-8421-faeb81a0bb51).|  
|Przestrzeń nazw|Zmienia nazwę przestrzeni nazw na nową nazwę w deklaracji, wszystkie `using` instrukcji i w pełni kwalifikowanych nazw. **Uwaga:**  Przy zmianie nazwy obszaru nazw, a [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aktualizuje również **domyślne Namespace** właściwość **aplikacji** strony **projektanta projektu**. Ta właściwość nie może być resetowany, wybierając **Cofnij** z **Edytuj** menu. Aby zresetować **domyślne Namespace** wartości właściwości, należy zmodyfikować właściwość w **projektanta projektu**. Aby uzyskać więcej informacji, zobacz [strony aplikacji](../ide/reference/application-page-project-designer-csharp.md).|  
|Właściwość|Zmienia deklaracji i użycia właściwości na nową nazwę.|  
|Typ|Zmienia wszystkie deklaracje i wszelkie użycia tego typu na nową nazwę, w tym konstruktory i destruktory. Dla typów częściowych operacji zmiany nazwy będzie propagowany do wszystkich części.|  
  
#### <a name="to-rename-an-identifier"></a>Aby zmienić nazwę identyfikatora  
  
1. Utwórz aplikację konsoli o nazwie `RenameIdentifier`, a następnie zastąp `Program` poniższym przykładowym kodem.  
  
    ```csharp  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2. Umieść kursor w `MethodB`, albo w deklaracji metody lub wywołania metody.  
  
3. Z **Refaktoryzuj** menu, wybierz opcję **Zmień nazwę**. **Zmień nazwę** pojawi się okno dialogowe.  
  
     Również kliknięciu prawym przyciskiem myszy kursora, wskaż polecenie **Refaktoryzuj** na menu kontekstowe, a następnie kliknij **Zmień nazwę** do wyświetlenia **Zmień nazwę** okno dialogowe.  
  
4. W **nową nazwę** wpisz `MethodC`.  
  
5. Wybierz **wyszukiwania w komentarzach** pole wyboru.  
  
6. Kliknij przycisk **OK**.  
  
7. W **podgląd zmian** okno dialogowe, kliknij przycisk **Zastosuj**.  
  
#### <a name="to-rename-an-identifier-using-smart-tags"></a>Aby zmienić nazwę identyfikatora przy użyciu tagów inteligentnych  
  
1. Utwórz aplikację konsoli o nazwie `RenameIdentifier`, a następnie zastąp `Program` poniższym przykładowym kodem.  
  
    ```csharp  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2. W deklaracji pod kątem `MethodB`, wpisz lub backspace za pośrednictwem identyfikatora metody. Poniżej tego identyfikatora, zostanie wyświetlony monit z tagu inteligentnego.  
  
    > [!NOTE]
    > Można wywołać tylko przy użyciu tagów inteligentnych na deklarację identyfikatora Refaktoryzacja zmiany nazwy.  
  
3. Wpisz skrót klawiaturowy, SHIFT + ALT + F10, a następnie naciśnij klawisz strzałki w dół, aby wyświetlić menu tagu inteligentnego.  
  
     —lub—  
  
     Przesuń wskaźnik myszy nad wiersz tagów inteligentnych do wyświetlenia tagu inteligentnego. Następnie przesuń wskaźnik myszy nad tagów inteligentnych i kliknij strzałkę w dół, aby wyświetlić menu tagu inteligentnego.  
  
4. Wybierz **Zmień nazwę "\<identifer1 >" do "\<identifier2 >"** element menu do wywołania, Refaktoryzacja zmiany nazwy bez podgląd zmian w kodzie. Wszystkie odwołania do  **\<identifer1 >** zostaną automatycznie zaktualizowane do  **\<identifier2 >**.  
  
     —lub—  
  
     Wybierz **Zmień Podgląd** element menu do wywołania, Refaktoryzacja zmiany nazwy z podgląd zmian w kodzie. **Podgląd zmian** zostanie wyświetlone okno dialogowe.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="renaming-implemented-or-overridden-members"></a>Zmiana nazwy elementów członkowskich implementowane lub zgodnym z Przesłoniętą  
 Po użytkownik **Zmień nazwę** elementu członkowskiego, która implementuje/zastąpienia lub zaimplementować/zastąpiona przez elementy członkowskie w innych typach [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wyświetlane jest okno dialogowe, informujący, że operacja zmiany nazwy spowoduje aktualizacji kaskadowych. Jeśli klikniesz **Kontynuuj**refaktoryzacji rekursywnie aparat wyszukuje i zmienia nazwę wszystkich elementów członkowskich w podstawowym i typy pochodne, które mają implementuje/zastąpienia relacji z elementem członkowskim nazwa jest zmieniana.  
  
 Poniższy przykład kodu zawiera elementy członkowskie z relacjami implementuje/zastąpień.  
  
 [!code-csharp[CsUsingCsIDERefactor#1](../snippets/csharp/VS_Snippets_VBCSharp/CsUsingCsIDERefactor/CS/Class1.cs#1)]  
  
 W poprzednim przykładzie zmiana nazwy `C.Method()` również zmienia nazwę `Ibase.Method()` ponieważ `C.Method()` implementuje `Ibase.Method()`. Następnie rekursywnie aparatu zrefaktoryzuj widzi, który `Ibase.Method()` jest implementowany przez `Derived.Method()` i zmienia nazwę `Derived.Method()`. Aparat refaktoryzacji nie powoduje zmiany nazwy `Base.Method()`, ponieważ `Derived.Method()` nie zastępuje `Base.Method()`. Aparat refaktoryzacji zatrzymuje się na nim chyba że masz **Zmień nazwę przeciążenia** zaewidencjonowany **Zmień nazwę** okno dialogowe.  
  
 Jeśli **Zmień nazwę przeciążenia** jest zaznaczona, zmienia nazwę aparatu zrefaktoryzuj `Derived.Method(int i)` ponieważ przeciąża `Derived.Method()`, `Base.Method(int i)` ponieważ zostanie on przesłonięty przez `Derived.Method(int i)`, i `Base.Method()` ponieważ przeciążenia `Base.Method(int i)`.  
  
> [!NOTE]
> Po zmianie nazwy elementu członkowskiego, która została zdefiniowana w zestawie odwołania, okno dialogowe wyjaśnia, że zmiana nazwy spowoduje błędy kompilacji.  
  
## <a name="renaming-properties-of-anonymous-types"></a>Zmiana nazwy właściwości anonimowych typów  
 Po zmianie nazwy właściwości anonimowych typów operacji zmiany nazwy będzie propagowany do właściwości na inne typy anonimowe, które mają te same właściwości. Poniższe przykłady pokazują to zachowanie.  
  
```csharp  
var a = new { ID = 1};  
var b = new { ID = 2};  
```  
  
 W poprzednim kodzie zmiana nazwy `ID` zmieni `ID` w obu deklaracjach ponieważ mają one ten sam typ podstawowy anonimowe.  
  
```csharp  
var companyIDs =  
    from c in companylist  
    select new { ID = c.ID, Name = c.Name};  
  
var orderIDs =  
    from o in orderlist  
    select new { ID = o.ID, Item = o.Name};  
```  
  
 W poprzednim kodzie zmiana nazwy `ID` tylko zmienić nazwę jednego wystąpienia `ID` ponieważ `companyIDs` i `orderIDs` nie mają tej samej właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Refaktoryzacja (C#)](../csharp-ide/refactoring-csharp.md)   
 [Typy anonimowe](http://msdn.microsoft.com/library/59c9d7a4-3b0e-475e-b620-0ab86c088e9b)