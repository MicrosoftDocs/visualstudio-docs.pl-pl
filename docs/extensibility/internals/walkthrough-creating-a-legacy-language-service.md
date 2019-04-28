---
title: 'Przewodnik: Tworzenie starszej wersji usługi językowej | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d58234dbe503f8d086e081464c2e38f759a75e3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62907924"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Przewodnik: Tworzenie starszej wersji usługi językowej
Używanie klas języka zarządzanego pakietu framework (MPF) do wdrożenia usługi w języka [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] jest bardzo proste. Należy VSPackage do hostowania usługi językowej, sama usługa języka i analizatora dla danego języka.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby skorzystać z tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../../extensibility/visual-studio-sdk.md).

## <a name="locations-for-the-visual-studio-package-project-template"></a>Lokalizacje szablon projektu pakietu Visual Studio
 Szablon projektu pakietu Visual Studio można znaleźć w trzech miejscach inny szablon w **nowy projekt** okno dialogowe:

1. W obszarze rozszerzalności programu Visual Basic. Domyślny język projektu jest języka Visual Basic.

2. W języku C# rozszerzalności. Domyślny język projektu jest C#.

3. W obszarze inne rozszerzalności typów projektów. Domyślny język projektu jest w języku C++.

### <a name="create-a-vspackage"></a>Tworzenie pakietu VSPackage

1. Tworzenie nowego pakietu VSPackage przy użyciu szablonu projektu pakietu Visual Studio.

    Jeśli usługa języka jest dodawane do istniejącego pakietu VSPackage, pominęli następujące kroki i przejść bezpośrednio do procedury "Tworzenie język usługi Class".

2. Wprowadź nazwę projektu MyLanguagePackage i kliknij przycisk **OK**.

    Można użyć dowolną nazwę. Te procedury przedstawione w tym miejscu założono MyLanguagePackage jako nazwę.

3. Wybierz [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] jako język i opcję, aby wygenerować nowy plik klucza. Kliknij przycisk **Dalej**.

4. Wprowadź odpowiednie informacje firmowe i pakietu. Kliknij przycisk **Dalej**.

5. Wybierz **polecenia Menu**. Kliknij przycisk **Dalej**.

    Jeśli nie zamierzasz obsługuje fragmenty kodu, można po prostu kliknij przycisk Zakończ i pomiń następny krok.

6. Wprowadź **Wstaw fragment kodu** jako **polecenia nazwa** i `cmdidInsertSnippet` dla **identyfikator polecenia**. Kliknij przycisk **Zakończ**.

    **Nazwa polecenia** i **identyfikator polecenia** może być dowolnie, Oto kilka przykładów.

### <a name="create-the-language-service-class"></a>Tworzenie klasy usługi w języka

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nad projektem MyLanguagePackage, wybierz pozycję **Dodaj**, **odwołania**, a następnie wybierz **Dodaj nowe odwołanie** przycisku.

2. W **Dodaj odwołanie** okno dialogowe, wybierz opcję **Microsoft.VisualStudio.Package.LanguageService** w **.NET** kartę, a następnie kliknij przycisk **OK**.

     To musi odbywać się tylko raz dla projektu pakietu języka.

3. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy dla projektu pakietu VSPackage i wybierz **Dodaj**, **klasy**.

4. Upewnij się, że **klasy** jest zaznaczony na liście szablonów.

5. Wprowadź **MyLanguageService.cs** dla nazwy pliku klasy i kliknij przycisk **Dodaj**.

     Można użyć dowolną nazwę. Te procedury przedstawione w tym miejscu przyjęto założenie `MyLanguageService` jako nazwę.

6. W pliku MyLanguageService.cs, Dodaj następujący kod `using` instrukcji.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]

7. Modyfikowanie `MyLanguageService` pochodzi od klasy <xref:Microsoft.VisualStudio.Package.LanguageService> klasy:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]

8. Umieść kursor na "LanguageService" i z **Edytuj**, **IntelliSense** menu, wybierz opcję **implementacji klasy abstrakcyjnej**. Spowoduje to dodanie minimalne metody niezbędne do zaimplementowania klasy usługi języka.

9. Implementują metody abstrakcyjne, zgodnie z opisem w [Implementowanie starszej wersji usługi językowej](../../extensibility/internals/implementing-a-legacy-language-service2.md).

### <a name="register-the-language-service"></a>Rejestrowanie usługi językowej

1. Otwórz plik MyLanguagePackagePackage.cs i Dodaj następujący kod `using` instrukcji:

     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]

2. Zarejestruj swoje klasy usługi w języka zgodnie z opisem w [rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md). W tym atrybuty ProvideXX i sekcji "Proffering usługa języka". Użyj MyLanguageService, w którym w tym temacie używany TestLanguageService.

### <a name="the-parser-and-scanner"></a>Analizator i skaner

1. Implementowanie analizator i skaner dla danego języka, zgodnie z opisem w [starszej wersji języka usługi analizator i skaner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

     Jak wdrożyć swoje analizator i skaner zależy od całkowicie użytkownika i wykracza poza zakres tego tematu.

## <a name="language-service-features"></a>Funkcje usługi w języka
 Aby zaimplementować każdą z funkcji w usłudze języka, zwykle wyprowadzenia klasy z odpowiedniej klasy usługi języka MPF, implementować wszystkie metody abstrakcyjne zgodnie z potrzebami i zastąpić odpowiedniej metody. Jakie klas, tworzenia i/lub pochodzić od jest zależna od funkcji użytkownik planuje pomocy technicznej. Te funkcje są szczegółowo omówione w [starszej wersji języka usługi funkcje](../../extensibility/internals/legacy-language-service-features1.md). Poniższa procedura dotyczy wyprowadzanie klasy z klas MPF ogólne podejście.

#### <a name="deriving-from-an-mpf-class"></a>Wyprowadzanie z klas MPF

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy dla projektu pakietu VSPackage i wybierz **Dodaj**, **klasy**.

2. Upewnij się, że **klasy** jest zaznaczony na liście szablonów.

     Wprowadź nazwę odpowiedniego pliku klasy, a następnie kliknij przycisk **Dodaj**.

3. W nowym pliku klasy, Dodaj następujący kod `using` instrukcji.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]

4. Modyfikuj klasę, aby dziedziczyć odpowiednią klasę MPF.

5. Dodaj konstruktora klasy, która ma co najmniej te same parametry jako konstruktor klasy bazowej i przekazywać parametry konstruktora do konstruktora klasy bazowej.

     Na przykład, Konstruktor dla klasy pochodnej z <xref:Microsoft.VisualStudio.Package.Source> klasy może wyglądać podobnie do poniższego:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]

6. Z **Edytuj**, **IntelliSense** menu, wybierz opcję **implementacji klasy abstrakcyjnej** Jeśli klasa bazowa ma metody abstrakcyjne, które muszą zostać zaimplementowane.

7. W przeciwnym razie pozycji karetki wewnątrz klasy i wejście do metody do zastąpienia.

     Na przykład wpisz `public override` umożliwia wyświetlenie listy wszystkich metod, które mogą zostać zastąpione przez tę klasę.

## <a name="see-also"></a>Zobacz też
- [Implementowanie starszej wersji usługi językowej](../../extensibility/internals/implementing-a-legacy-language-service1.md)