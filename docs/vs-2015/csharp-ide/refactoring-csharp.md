---
title: Refaktoryzacja (C#) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.csharp.refactoring.preview
- vs.csharp.refactoring.issues
- vs.csharp.refactoring.buildwarning
- VS.PreviewChanges
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#]
ms.assetid: a39e656a-f81f-4c87-b484-a23168ff1dfc
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 78ac19ac0e992b51affdbf6a0e6e3268ddfa52d0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54785467"
---
# <a name="refactoring-c"></a>Refaktoryzacja (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Refaktoryzacja to proces po została zapisana przez zmianę wewnętrznej struktury kodu bez zmiany zachowania zewnętrznego kodu w celu ulepszania kodu.  
  
 Visual C# zawiera następujące polecenia refaktoryzacji **Refactoring** menu:  
  
-   [Refaktoryzacja wyodrębniania metody (C#)](../csharp-ide/extract-method-refactoring-csharp.md)  
  
-   [Refaktoryzacja zmiany nazwy (C#)](../csharp-ide/rename-refactoring-csharp.md)  
  
-   [Refaktoryzacja hermetyzowania pola (C#)](../csharp-ide/encapsulate-field-refactoring-csharp.md)  
  
-   [Refaktoryzacja wyodrębniania interfejsu (C#)](../csharp-ide/extract-interface-refactoring-csharp.md)  
  
-   [Refaktoryzacja usuwania parametrów (C#)](../csharp-ide/remove-parameters-refactoring-csharp.md)  
  
-   [Refaktoryzacja zmiany kolejności parametrów (C#)](../csharp-ide/reorder-parameters-refactoring-csharp.md)  
  
## <a name="multi-project-refactoring"></a>Refaktoryzacja wielu projektów  
 Program Visual Studio obsługuje wielu projektów, Refaktoryzacja dla projektów, które znajdują się w tym samym rozwiązaniu. Wszystkie operacje refaktoryzacji, które poprawić odwołań między plikami Popraw te odwołania we wszystkich projektach tego samego języka. Działa to w przypadku dowolnego odwołania projekt projekt. Na przykład, jeśli masz aplikację konsolową, która odwołuje się do biblioteki klas, po zmianie nazwy typu klasy biblioteki (przy użyciu `Rename` operacja refaktoryzacji), odwołania do typu biblioteki klas w aplikacji konsolowej również są aktualizowane.  
  
## <a name="changes-preview"></a>Podgląd zmian  
 Wiele operacji refaktoryzacji zapewnienia możliwości dla Ciebie przejrzeć wszystkie odwołania wprowadzone operacji refaktoryzacji wykona przed zatwierdzeniem tych zmian w kodzie. Te operacje, refaktoryzacji **podgląd zmian odwołań** opcja jest wyświetlana w oknie dialogowym refaktoryzacji. Po wybraniu tej opcji, a następnie akceptując operacji refaktoryzacji **okno dialogowe zmiany wersji zapoznawczej** będą wyświetlane. Należy zauważyć, że **podgląd zmian** okno dialogowe ma dwa widoki. Widok dołu zawiera kod dla wszystkich aktualizacji odwołania z powodu operacji refaktoryzacji. Naciśnięcie klawisza **anulować** na **podgląd zmian** okno dialogowe przestanie operacji refaktoryzacji, a zostaną wprowadzone nie zmiany w kodzie.  
  
## <a name="refactoring-warnings"></a>Refaktoryzacja ostrzeżenia  
 Jeśli kompilator nie ma dokładnego zrozumienia działania programu i jest możliwe, aparat refaktoryzacji może nie zaktualizować wszystkie odpowiednie odwołania, zostanie wyświetlone okno dialogowe ostrzeżenia. To okno dialogowe Ostrzeżenie udostępnia również możliwość nad wersją zapoznawczą swój kod w **podgląd zmian** okno dialogowe, aby zatwierdzić zmiany.  
  
> [!NOTE]
>  Jeśli metoda zawiera błąd składniowy (która IDE wskazuje czerwoną linią falistą), następnie aparat refaktoryzacji nie zaktualizuje wszystkie odwołania do elementu w ramach tej metody. W poniższym przykładzie przedstawiono to zachowanie.  
  
 Domyślnie jeśli można wykonać operacji refaktoryzacji, bez odwołania podgląd zmian wykryto błąd kompilacji w programie, a następnie środowisko programistyczne wyświetla to okno dialogowe ostrzeżenia.  
  
 Jeśli zostanie wykonana operacja refaktoryzacji, która ma **podgląd zmian odwołania** włączone wykryto błąd kompilacji w programie, a następnie środowisko programistyczne wyświetli następujący komunikat ostrzegawczy w dolnej części **Podgląd zmian** okno dialogowe, zamiast wyświetlania **refaktoryzacji ostrzeżenie** okno dialogowe:  
  
 **Projekt lub jeden z jego elementów zależnych nie aktualnie są kompilowane. Odwołania nie może zostać zaktualizowany.**  
  
 To ostrzeżenie refaktoryzacji jest dostępna tylko dla operacji refaktoryzacji, które zapewniają **podgląd zmian odwołania** opcji.  
  
## <a name="error-tolerant-refactoring-and-verification-results"></a>Refaktoryzacja błąd odpornej na uszkodzenia i wyniki weryfikacji  
 Refaktoryzacja błędu odpornego na błędy. Innymi słowy można wykonać, Refaktoryzacja w projekcie, który nie może utworzyć. Jednak w tych przypadkach proces refaktoryzacji może nie zaktualizować niejednoznacznego odwołania poprawnie.  
  
 **Wyniki weryfikacji** okno dialogowe może powiadomić refaktoryzacji engine wykrywa błędy kompilacji lub wykrywa, że operacja refaktoryzacji przypadkowo powoduje, że odwołanie kodu można coś, co różni się od go powiązać pierwotnie powiązany (ponowne wiązanie problem).  
  
 Aby włączyć wyniki weryfikacji funkcji na **narzędzia** menu, kliknij przycisk **opcje**. W **opcje** okna dialogowego rozwiń **edytora tekstów**, a następnie rozwiń węzeł **C#**. Kliknij przycisk **zaawansowane** i wybierz **Sprawdź wyniki refaktoryzacji** pole wyboru.  
  
 **Wyniki weryfikacji** okno dialogowe wyróżnia różnicę między dwoma rodzajami ponowne wiązanie problemów.  
  
### <a name="references-whose-definition-will-no-longer-be-the-renamed-symbol"></a>Odwołania, którego definicja nie będzie już zmieniono nazwy symbolu  
 Tego rodzaju ponowne powiązywanie problem występuje, gdy odwołanie nie odwołuje się już do zmieniono nazwę symbolu. Na przykład rozważmy następujący kod:  
  
```csharp  
class Example  
{  
    private int a;  
    public Example(int b)  
    {  
        a = b;  
    }  
}  
```  
  
 Jeśli używasz Refaktoryzacja zmiany nazwy `a` do `b`, pojawi się okno dialogowe. Odwołanie do zmiennej których nazwy zostały zmienione `a` teraz wiąże parametr, który jest przekazywany do konstruktora zamiast powiązania do pola.  
  
### <a name="references-whose-definition-will-now-become-the-renamed-symbol"></a>Odwołania, którego definicja, stanie się zmieniło nazwę symbolu  
 Tego rodzaju ponowne powiązywanie problem występuje, gdy odwołanie, którego wcześniej nie odwołuje się do symbolu zmienionej nazwie teraz odwołuje się do symbolu, których nazwy zostały zmienione. Na przykład rozważmy następujący kod:  
  
```csharp  
class Example  
{  
    private static void Method(object a) { }  
    private static void OtherMethod(int a) { }  
    static void Main(string[] args)  
    {  
        Method(5);  
    }  
}  
```  
  
 Jeśli używasz Refaktoryzacja zmiany nazwy `OtherMethod` do `Method`, pojawi się okno dialogowe. Odwołania w `Main` teraz odwołuje się do metody przeciążonej, który akceptuje `int` parametru zamiast przeciążona metoda, która akceptuje `object` parametru.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie środowiska programistycznego Visual Studio dla języka C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)   
 [Instrukcje: Przywróć C# Refaktoryzowanych wstawek kodu](../ide/how-to-restore-csharp-refactoring-snippets.md)