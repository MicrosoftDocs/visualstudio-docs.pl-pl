---
title: 'Przewodnik: Tworzenie usługi języka starszego | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59ec18ab0c97ec89422e06f5b33804adcc750d5a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703687"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Przewodnik: tworzenie starszej wersji usługi językowej
Za pomocą klasy języka struktury pakietu zarządzanego (MPF) do zaimplementowania usługi języka w [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] jest prosta. Potrzebujesz vspackage do obsługi usługi języka, samej usługi języka i analizatora dla języka.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby wykonać ten przewodnik, należy zainstalować visual studio SDK. Aby uzyskać więcej informacji, zobacz [Visual Studio SDK](../../extensibility/visual-studio-sdk.md).

## <a name="locations-for-the-visual-studio-package-project-template"></a>Lokalizacje dla szablonu projektu pakietu programu Visual Studio
 Szablon projektu pakietu programu Visual Studio można znaleźć w trzech różnych lokalizacjach szablonów w oknie dialogowym **Nowy projekt:**

1. W obszarze Rozszerzalność języka Visual Basic. Domyślnym językiem projektu jest visual basic.

2. W obszarze C# Rozszerzalność. Domyślnym językiem projektu jest C#.

3. W obszarze Rozszerzalność innych typów projektów. Domyślnym językiem projektu jest C++.

### <a name="create-a-vspackage"></a>Tworzenie pakietu VSPackage

1. Utwórz nowy pakiet VSPackage z szablonem projektu pakietu programu Visual Studio.

    Jeśli dodajesz usługę języka do istniejącego pakietu VSPackage, pomiń następujące kroki i przejdź bezpośrednio do procedury "Utwórz klasę usługi językowej".

2. Wprowadź MyLanguagePackage dla nazwy projektu i kliknij **PRZYCISK OK**.

    Możesz użyć dowolnej nazwy. Te procedury szczegółowe tutaj zakład mylanguagePackage jako nazwę.

3. Wybierz [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] jako język i opcję wygenerowania nowego pliku klucza. Kliknij przycisk **Dalej**.

4. Wprowadź odpowiednie informacje o firmie i pakiecie. Kliknij przycisk **Dalej**.

5. Wybierz **polecenie menu**. Kliknij przycisk **Dalej**.

    Jeśli nie zamierzasz obsługiwać fragmentów kodu, możesz po prostu kliknąć przycisk Zakończ i zignorować następny krok.

6. Wprowadź **fragment kodu wstaw** jako `cmdidInsertSnippet` nazwę **polecenia** i identyfikator **polecenia**. Kliknij przycisk **Zakończ**.

    **Nazwa polecenia** i **identyfikator polecenia** może być cokolwiek chcesz, są to tylko przykłady.

### <a name="create-the-language-service-class"></a>Tworzenie klasy usługi językowej

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt MyLanguagePackage, wybierz polecenie **Dodaj**, **Odwołanie**, a następnie wybierz przycisk Dodaj **nowe odwołanie.**

2. W oknie dialogowym **Dodawanie odwołania** wybierz pozycję **Microsoft.VisualStudio.Package.LanguageService** na karcie **.NET** i kliknij przycisk **OK**.

     Należy to zrobić tylko raz dla projektu pakietu językowego.

3. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt VSPackage i wybierz polecenie **Dodaj**, **Klasa**.

4. Upewnij się, że na liście szablonów wybrano opcję **Klasa.**

5. Wprowadź **MyLanguageService.cs** dla nazwy pliku klasy i kliknij przycisk **Dodaj**.

     Możesz użyć dowolnej nazwy. Te procedury `MyLanguageService` opisane w tym miejscu przyjąć jako nazwę.

6. W pliku MyLanguageService.cs dodaj następujące `using` dyrektywy.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]

7. Zmodyfikuj `MyLanguageService` klasę, aby wyprowadzić się <xref:Microsoft.VisualStudio.Package.LanguageService> z klasy:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]

8. Umieść kursor w "LanguageService" i z menu **Edycja**, **IntelliSense** wybierz pozycję **Implementuj klasę abstrakcyjną**. Spowoduje to dodanie minimalnych metod niezbędnych do zaimplementowania klasy usługi języka.

9. Zaimplementuj metody abstrakcyjne, jak opisano w [implementacji usługi języka starszego](../../extensibility/internals/implementing-a-legacy-language-service2.md).

### <a name="register-the-language-service"></a>Zarejestruj usługę językową

1. Otwórz plik MyLanguagePackagePackage.cs i dodaj następujące `using` dyrektywy:

     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]

2. Zarejestruj klasę usługi językowej zgodnie z opisem w [rejestrze usługi języka starszego.](../../extensibility/internals/registering-a-legacy-language-service1.md) Obejmuje to atrybuty ProvideXX i sekcje "Proffering the Language Service". Użyj MyLanguageService, gdzie ten temat używa TestLanguageService.

### <a name="the-parser-and-scanner"></a>Analizator i skaner

1. Zaimplementuj analizator i skaner dla swojego języka, jak opisano w starszej usługi [parsera i skanera](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

     Jak zaimplementować analizatora i skanera jest całkowicie do Ciebie i wykracza poza zakres tego tematu.

## <a name="language-service-features"></a>Funkcje usługi językowej
 Aby zaimplementować każdą funkcję w usłudze języka, zazwyczaj można wyprowadzić klasę z odpowiedniej klasy usługi języka MPF, zaimplementować wszystkie metody abstrakcyjne w razie potrzeby i zastąpić odpowiednie metody. Klasy, które tworzysz i/lub z których czerpiesz, zależą od funkcji, które mają być obsługiwane. Te funkcje zostały szczegółowo omówione w [starszych funkcjach usługi języka](../../extensibility/internals/legacy-language-service-features1.md). Poniższa procedura jest ogólne podejście do wyprowadzania klasy z mpf klas.

#### <a name="deriving-from-an-mpf-class"></a>Wyprowadzenie z klasy MPF

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt VSPackage i wybierz polecenie **Dodaj**, **Klasa**.

2. Upewnij się, że na liście szablonów wybrano opcję **Klasa.**

     Wprowadź odpowiednią nazwę pliku klasy i kliknij przycisk **Dodaj**.

3. W pliku nowej klasy dodaj `using` następujące dyrektywy.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]

4. Zmodyfikuj klasę, aby pochodzić z żądanej klasy MPF.

5. Dodaj konstruktora klasy, który przyjmuje co najmniej te same parametry co konstruktor klasy podstawowej i przekazuje parametry konstruktora do konstruktora klasy podstawowej.

     Na przykład konstruktor dla klasy pochodnej <xref:Microsoft.VisualStudio.Package.Source> z klasy może wyglądać następująco:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]

6. Z menu **Edycja**, **IntelliSense** wybierz opcję **Implementuj klasę abstrakcyjną,** jeśli klasa podstawowa ma jakieś abstrakcyjne metody, które muszą zostać zaimplementowane.

7. W przeciwnym razie umieść cieszę wewnątrz klasy i wprowadź metodę, która ma zostać zastąpiona.

     Na przykład `public override` wpisz, aby wyświetlić listę wszystkich metod, które mogą być zastąpione w tej klasie.

## <a name="see-also"></a>Zobacz też
- [Implementowanie starszej wersji usługi językowej](../../extensibility/internals/implementing-a-legacy-language-service1.md)
