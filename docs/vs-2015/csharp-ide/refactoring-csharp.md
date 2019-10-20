---
title: Refaktoryzacja (C#) | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0415222645dce2f65e91b5b1c55a5a118cc26697
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667503"
---
# <a name="refactoring-c"></a>Refaktoryzacja (C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Refaktoryzacja to proces ulepszania kodu po jego zapisaniu przez zmianę wewnętrznej struktury kodu bez zmiany zewnętrznego zachowania kodu.

 Wizualizacja C# udostępnia następujące polecenia refaktoryzacji w menu **refaktoryzacji** :

- [Refaktoryzacja wyodrębniania metody (C#)](../csharp-ide/extract-method-refactoring-csharp.md)

- [Refaktoryzacja zmiany nazwy (C#)](../csharp-ide/rename-refactoring-csharp.md)

- [Refaktoryzacja hermetyzowania pola (C#)](../csharp-ide/encapsulate-field-refactoring-csharp.md)

- [Refaktoryzacja wyodrębniania interfejsu (C#)](../csharp-ide/extract-interface-refactoring-csharp.md)

- [Refaktoryzacja usuwania parametrów (C#)](../csharp-ide/remove-parameters-refactoring-csharp.md)

- [Refaktoryzacja zmiany kolejności parametrów (C#)](../csharp-ide/reorder-parameters-refactoring-csharp.md)

## <a name="multi-project-refactoring"></a>Refaktoryzacja wieloprojektowa
 Program Visual Studio obsługuje refaktoryzację wieloprojektową dla projektów, które znajdują się w tym samym rozwiązaniu. Wszystkie operacje refaktoryzacji, które korygują odwołania w plikach, korygują te odwołania we wszystkich projektach tego samego języka. Działa to w przypadku wszystkich odwołań między projektami. Na przykład jeśli masz aplikację konsolową, która odwołuje się do biblioteki klas, podczas zmiany nazwy typu biblioteki klas (przy użyciu operacji refaktoryzacji `Rename`) odwołania do typu biblioteki klas w aplikacji konsolowej również zostaną zaktualizowane.

## <a name="changes-preview"></a>Podgląd zmian
 Wiele operacji refaktoryzacji daje możliwość przejrzenia wszystkich zmian odniesienia, które wykonuje operacja refaktoryzacji w kodzie, przed zatwierdzeniem zmian. W przypadku tych operacji refaktoryzacji w oknie dialogowym Refaktoryzacja zostanie wyświetlona opcja **Podgląd zmian odwołania** . Po wybraniu tej opcji i zaakceptowaniu operacji refaktoryzacji zostanie wyświetlone okno **dialogowe Podgląd zmian** . Zwróć uwagę, że okno dialogowe **Podgląd zmian** ma dwa widoki. W dolnym widoku zostanie wyświetlony kod ze wszystkimi aktualizacjami odwołań spowodowanymi operacją refaktoryzacji. Naciśnięcie przycisku **Anuluj** w oknie dialogowym **Podgląd zmian** spowoduje zatrzymanie operacji refaktoryzacji i wprowadzenie zmian w kodzie nie będzie możliwe.

## <a name="refactoring-warnings"></a>Ostrzeżenia refaktoryzacji
 Jeśli kompilator nie ma kompletnego rozumienia programu i istnieje możliwość, że aparat refaktoryzacji może nie zaktualizować wszystkich odpowiednich odwołań, wyświetlane jest okno dialogowe ostrzeżenia. To okno dialogowe ostrzeżenia umożliwia również wyświetlenie podglądu kodu w oknie dialogowym **zmiany w wersji zapoznawczej** przed zatwierdzeniem zmian.

> [!NOTE]
> Jeśli metoda zawiera błąd składniowy (który IDE wskazuje czerwoną linią falistą), aparat refaktoryzacji nie zaktualizuje żadnych odwołań do elementu w tej metodzie. Poniższy przykład ilustruje to zachowanie.

 Domyślnie, jeśli wykonujesz operację refaktoryzacji bez wyświetlania podglądów zmian odwołań i w programie wykryto błąd kompilacji, środowisko programistyczne wyświetla to okno dialogowe ostrzeżenia.

 Jeśli wykonujesz operację refaktoryzacji, która ma włączone **zmiany w wersji zapoznawczej** , a w programie wykryto błąd kompilacji, w środowisku deweloperskim zostanie wyświetlony następujący komunikat ostrzegawczy dotyczący zmiany w **wersji zapoznawczej** zamiast wyświetlania okna dialogowego **ostrzeżenia refaktoryzacji** :

 **Projekt lub jedna z jej zależności nie jest obecnie kompiluje. Odwołania nie mogą zostać zaktualizowane.**

 To ostrzeżenie refaktoryzacji jest dostępne tylko w przypadku operacji refaktoryzacji, które udostępniają opcję **zmiany w wersji zapoznawczej** .

## <a name="error-tolerant-refactoring-and-verification-results"></a>Refaktoryzacja odporna na błędy i wyniki weryfikacji
 Refaktoryzacja jest odporna na błędy. Innymi słowy, można wykonać refaktoryzację w projekcie, który nie może skompilować. Jednak w takich przypadkach proces refaktoryzacji nie może poprawnie aktualizować niejednoznacznych odwołań.

 W oknie dialogowym **wyniki weryfikacji** można powiadomić użytkownika, jeśli aparat refaktoryzacji wykryje błędy kompilacji lub odkryje, że operacja refaktoryzacji nieumyślnie powoduje powiązanie kodu z czymś innym niż to, z jakim było pierwotnie powiązane. ponowne wiązanie problemu).

 Aby włączyć funkcję wyniki weryfikacji, w menu **Narzędzia** kliknij polecenie **Opcje**. W oknie dialogowym **Opcje** rozwiń pozycję **Edytor tekstu**, a następnie rozwiń węzeł **C#** . Kliknij przycisk **Zaawansowane** i zaznacz pole wyboru **Weryfikuj wyniki refaktoryzacji** .

 W oknie dialogowym **wyniki weryfikacji** rozróżniana jest różnica między dwoma rodzajami problemów związanych z łączeniem.

### <a name="references-whose-definition-will-no-longer-be-the-renamed-symbol"></a>Odwołania, których definicja nie będzie już symbolem zmiany nazwy
 Ten rodzaj problemu ponownego powiązania występuje, gdy odwołanie nie odwołuje się już do symbolu o zmienionej nazwie. Rozważmy na przykład następujący kod:

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

 Jeśli użyjesz refaktoryzacji, aby zmienić nazwę `a` na `b`, zostanie wyświetlone okno dialogowe. Odwołanie do zmiennej o zmienionej nazwie `a` teraz wiąże się z parametrem, który jest przesyłany do konstruktora zamiast do powiązania z polem.

### <a name="references-whose-definition-will-now-become-the-renamed-symbol"></a>Odwołania, których definicja stanie się teraz symbolem o zmienionej nazwie
 Ten rodzaj problemu ponownego powiązania występuje, gdy odwołanie, które wcześniej nie odwołuje się do symbolu o zmienionej nazwie, odwołuje się do symbolu o zmienionej nazwie. Rozważmy na przykład następujący kod:

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

 Jeśli użyjesz refaktoryzacji, aby zmienić nazwę `OtherMethod` na `Method`, zostanie wyświetlone okno dialogowe. Odwołanie w `Main` teraz odwołuje się do przeciążonej metody, która akceptuje parametr `int` zamiast przeciążonej metody, która akceptuje parametr `object`.

## <a name="see-also"></a>Zobacz też
 [Używanie środowiska deweloperskiego programu Visual Studio C# na potrzeby](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md) [: Przywracanie C# fragmentów kodu refaktoryzacji](../ide/how-to-restore-csharp-refactoring-snippets.md)