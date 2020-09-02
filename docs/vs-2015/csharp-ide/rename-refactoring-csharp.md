---
title: Refaktoryzacja zmiany nazwy (C#) | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0db7696268e5e3d24d005fbf35a08b330f2dc849
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667476"
---
# <a name="rename-refactoring-c"></a>Refaktoryzacja zmiany nazwy (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Zmiana nazwy** to funkcja refaktoryzacji w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio, która zapewnia łatwy sposób zmiany nazw identyfikatorów dla symboli kodu, takich jak pola, zmienne lokalne, metody, przestrzenie nazw, właściwości i typy. **Nazwy** można użyć do zmiany nazw w komentarzach i w ciągach oraz do zmiany deklaracji i wywołań identyfikatora.

> [!NOTE]
> W przypadku korzystania z kontroli źródła dla programu Visual Studio przed podjęciem próby przeprowadzenia refaktoryzacji zmiany nazwy Pobierz najnowszą wersję źródeł.

 Refaktoryzacja zmiany nazwy jest dostępna w następujących funkcjach programu Visual Studio:

|Cechy|Zachowanie refaktoryzacji w IDE|
|-------------|----------------------------------------|
|Edytor kodu|W edytorze kodu Refaktoryzacja zmiany nazwy jest dostępna po umieszczeniu kursora na niektórych typach symboli kodu. Gdy kursor znajduje się w tym miejscu, możesz wywołać polecenie **zmiany nazwy** , wpisując skrót klawiaturowy (Ctrl + r, Ctrl + r) lub wybierając polecenie **Zmień nazwę** z tagu inteligentnego, menu skrótów lub menu **refaktoryzacji** .|
|Widok klas|Po wybraniu identyfikatora w Widok klasy, Refaktoryzacja zmiany nazwy jest dostępna z menu skrótów i menu **refaktoryzacji** .|
|Przeglądarka obiektów|Po wybraniu identyfikatora w Przeglądarka obiektów, Refaktoryzacja zmiany nazwy jest dostępna tylko w menu **refaktoryzacji** .|
|Siatka właściwości Projektant formularzy systemu Windows|W **siatce właściwości** Projektant formularzy systemu Windows zmiana nazwy kontrolki spowoduje zainicjowanie operacji zmiany nazwy dla tej kontrolki. Nie zostanie wyświetlone okno dialogowe **Zmień nazwę** .|
|Eksplorator rozwiązań|W **Eksplorator rozwiązań**polecenie **zmiany nazwy** jest dostępne w menu skrótów. Jeśli wybrany plik źródłowy zawiera klasę, której nazwa klasy jest taka sama jak nazwa pliku, można użyć tego polecenia, aby jednocześnie zmienić nazwę pliku źródłowego i wykonać refaktoryzację zmiany nazwy.<br /><br /> Jeśli na przykład utworzysz domyślną aplikację opartą na systemie Windows, a następnie zmienisz nazwę Form1.cs na TestForm.cs, nazwa pliku źródłowego Form1.cs zmieni się na TestForm.cs, a Klasa Form1 i wszystkie odwołania do tej klasy zostaną zmienione na TestForm. **Uwaga:**  Polecenie **Cofnij** (Ctrl + Z) spowoduje cofnięcie refaktoryzacji zmiany nazwy w kodzie i nie spowoduje zmiany nazwy pliku z powrotem na oryginalną nazwę. <br /><br /> Jeśli wybrany plik źródłowy nie zawiera klasy, której nazwa jest taka sama jak nazwa pliku, polecenie **zmiany nazwy** w **Eksplorator rozwiązań** będzie zmieniać nazwę pliku źródłowego i nie będzie wykonywał refaktoryzacji zmiany nazwy.|

## <a name="rename-operations"></a>Operacje zmiany nazwy
 Po wykonaniu **zmiany nazwy**aparat refaktoryzacji wykonuje operację zmiany nazwy specyficzną dla każdego symbolu kodu, zgodnie z opisem w poniższej tabeli.

|Symbol kodu|Zmień nazwę operacji|
|-----------------|----------------------|
|Pole|Zmienia deklarację i użycie pola na nową nazwę.|
|Zmienna lokalna|Zmienia deklarację i użycie zmiennej na nową nazwę.|
|Metoda|Zmienia nazwę metody i wszystkie odwołania do tej metody na nową nazwę. **Uwaga:**  Po zmianie nazwy metody rozszerzenia operacja zmiany nazwy jest propagowana do wszystkich wystąpień metody, które znajdują się w zakresie, niezależnie od tego, czy Metoda rozszerzenia jest używana jako metoda statyczna czy metoda wystąpienia. Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](https://msdn.microsoft.com/library/175ce3ff-9bbf-4e64-8421-faeb81a0bb51).|
|Przestrzeń nazw|Zmienia nazwę przestrzeni nazw na nową nazwę w deklaracji, wszystkie `using` instrukcje i w pełni kwalifikowanych nazw. **Uwaga:**  Podczas zmieniania nazwy przestrzeni nazw program [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aktualizuje także **domyślną właściwość przestrzeni nazw** na stronie **aplikacji** **projektanta projektu**. Tej właściwości nie można zresetować, wybierając polecenie **Cofnij** z menu **Edycja** . Aby zresetować domyślną wartość właściwości **Namespace** , należy zmodyfikować właściwość w **projektancie projektu**. Aby uzyskać więcej informacji, zobacz [stronę aplikacji](../ide/reference/application-page-project-designer-csharp.md).|
|Właściwość|Zmienia deklarację i użycia właściwości na nową nazwę.|
|Typ|Zmienia wszystkie deklaracje i wszystkie użycia typu na nową nazwę, w tym konstruktory i destruktory. W przypadku typów częściowych operacja zmiany nazwy będzie propagowana do wszystkich części.|

#### <a name="to-rename-an-identifier"></a>Aby zmienić nazwę identyfikatora

1. Utwórz aplikację konsolową o nazwie `RenameIdentifier` , a następnie zastąp ciąg `Program` następującym przykładowym kodem.

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

2. Umieść kursor na `MethodB` , w deklaracji metody lub wywołaniu metody.

3. W menu **refaktoryzacji** wybierz pozycję **Zmień nazwę**. Zostanie wyświetlone okno dialogowe **zmiana nazwy** .

     Możesz również kliknąć prawym przyciskiem myszy kursor, wskazać polecenie **Refaktoryzacja** w menu kontekstowym, a następnie kliknąć polecenie **Zmień nazwę** , aby wyświetlić okno dialogowe **Zmień nazwę** .

4. W polu **Nowa nazwa** wpisz `MethodC` .

5. Zaznacz pole wyboru **Wyszukaj w komentarzach** .

6. Kliknij przycisk **OK**.

7. W oknie dialogowym **Podgląd zmian** kliknij przycisk **Zastosuj**.

#### <a name="to-rename-an-identifier-using-smart-tags"></a>Aby zmienić nazwę identyfikatora przy użyciu tagów inteligentnych

1. Utwórz aplikację konsolową o nazwie `RenameIdentifier` , a następnie zastąp ciąg `Program` następującym przykładowym kodem.

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

2. W deklaracji dla `MethodB` , wpisz lub Backspace przy użyciu identyfikatora metody. Zostanie wyświetlony monit tagu inteligentnego poniżej tego identyfikatora.

    > [!NOTE]
    > Refaktoryzację zmiany nazwy można wywołać tylko przy użyciu tagów inteligentnych w deklaracji identyfikatora.

3. Wpisz skrót klawiaturowy SHIFT + ALT + F10, a następnie naciśnij strzałkę w dół, aby wyświetlić menu tagu inteligentnego.

     -lub-

     Przesuń wskaźnik myszy nad wiersz tagu inteligentnego, aby wyświetlić tag inteligentny. Następnie przesuń wskaźnik myszy nad tag inteligentny i kliknij strzałkę w dół, aby wyświetlić menu tagu inteligentnego.

4. Wybierz element menu **Zmień nazwę " \<identifer1> " \<identifier2> na "** , aby wywołać refaktoryzację zmiany nazwy bez podglądu zmian wprowadzonych w kodzie. Wszystkie odwołania do **\<identifer1>** zostaną automatycznie zaktualizowane do **\<identifier2>** .

     -lub-

     Wybierz pozycję **Zmień nazwę z menu Podgląd** , aby wywołać refaktoryzację zmiany nazwy z podglądem zmian wprowadzonych w kodzie. Zostanie wyświetlone okno dialogowe **Podgląd zmian** .

## <a name="remarks"></a>Uwagi

## <a name="renaming-implemented-or-overridden-members"></a>Zmiana nazwy zaimplementowanych lub zastąpionych elementów członkowskich
 Po **zmianie nazwy** elementu członkowskiego, który implementuje/zastępuje lub jest zaimplementowany/przesłonięty przez elementy członkowskie w innych typach, program [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wyświetli okno dialogowe z informacją, że operacja zmiany nazwy będzie powodowała aktualizacje kaskadowe. Jeśli klikniesz pozycję **Kontynuuj**, aparat refaktoryzacji rekursywnie odnajdzie i zmieni nazwy wszystkich elementów członkowskich w typach podstawowych i pochodnych, które mają relacje Implementuj/override z elementem członkowskim, którego nazwa jest zmieniana.

 Poniższy przykład kodu zawiera elementy członkowskie z relacjami IMPLEMENT/Overrides.

 [!code-csharp[CsUsingCsIDERefactor#1](../snippets/csharp/VS_Snippets_VBCSharp/CsUsingCsIDERefactor/CS/Class1.cs#1)]

 W poprzednim przykładzie zmiana nazwy również jest zmieniana, `C.Method()` `Ibase.Method()` ponieważ `C.Method()` implementuje `Ibase.Method()` . Następnie aparat refaktoryzacji rekursywnie widzi, że `Ibase.Method()` jest zaimplementowany przez `Derived.Method()` i zmienia nazwy `Derived.Method()` . Nie można zmienić nazwy aparatu refaktoryzacji `Base.Method()` , ponieważ nie zostanie `Derived.Method()` on przesłonięty `Base.Method()` . Aparat refaktoryzacji kończy się w tym miejscu, chyba że w oknie dialogowym **zmiana nazwy** zaznaczono opcję **przeciążenia zmiany nazwy** .

 Jeśli jest zaznaczone **przeciążanie zmiany nazwy** , aparat refaktoryzacji zmienia nazwę, `Derived.Method(int i)` ponieważ przeciąża `Derived.Method()` , `Base.Method(int i)` ponieważ jest zastępowany przez `Derived.Method(int i)` , i `Base.Method()` ponieważ jest przeciążeniem `Base.Method(int i)` .

> [!NOTE]
> Po zmianie nazwy elementu członkowskiego, który został zdefiniowany w przywoływanym zestawie, w oknie dialogowym objaśniono, że zmiana nazwy spowoduje błędy kompilacji.

## <a name="renaming-properties-of-anonymous-types"></a>Zmienianie nazw właściwości typów anonimowych
 Po zmianie nazwy właściwości w typach anonimowych operacja zmiany nazwy będzie propagowana do właściwości w innych typach anonimowych, które mają te same właściwości. Poniższe przykłady ilustrują to zachowanie.

```csharp
var a = new { ID = 1};
var b = new { ID = 2};
```

 W powyższym kodzie zmiany nazwy `ID` zmienią się `ID` w obu instrukcjach, ponieważ mają taki sam typ anonimowy.

```csharp
var companyIDs =
    from c in companylist
    select new { ID = c.ID, Name = c.Name};

var orderIDs =
    from o in orderlist
    select new { ID = o.ID, Item = o.Name};
```

 W poprzednim kodzie zmiana nazwy `ID` będzie miała nazwę tylko jedno wystąpienie z, `ID` ponieważ `companyIDs` `orderIDs` nie ma takich samych właściwości.

## <a name="see-also"></a>Zobacz też
 [Typy anonimowe](https://msdn.microsoft.com/library/59c9d7a4-3b0e-475e-b620-0ab86c088e9b) [(C#)](../csharp-ide/refactoring-csharp.md)