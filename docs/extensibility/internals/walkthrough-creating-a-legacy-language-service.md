---
title: 'Przewodnik: Tworzenie starszej wersji usługi językowej | Microsoft Docs'
description: Dowiedz się, jak wdrożyć usługę języka w języku Visual C# przy użyciu klas języka struktury zarządzanego pakietu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ded5624aed40ac2e878c44fd8dabc7d35c4d1ac8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074278"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Przewodnik: Tworzenie starszej wersji usługi językowej
Korzystanie z klas języka Managed Package Framework (MPF) w celu zaimplementowania usługi językowej w programie [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] jest proste. Potrzebujesz pakietu VSPackage do hostowania usługi językowej, samej usługi językowej i analizatora dla danego języka.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby wykonać czynności opisane w tym przewodniku, należy zainstalować Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [Visual Studio SDK](../../extensibility/visual-studio-sdk.md).

## <a name="locations-for-the-visual-studio-package-project-template"></a>Lokalizacje szablonu projektu pakietu programu Visual Studio
 Szablon projektu pakietu programu Visual Studio można znaleźć w trzech różnych lokalizacjach szablonów w oknie dialogowym **Nowy projekt** :

1. W obszarze rozszerzalność Visual Basic. Domyślny język projektu jest Visual Basic.

2. W obszarze rozszerzalność języka C#. Językiem domyślnym projektu jest C#.

3. W obszarze Inne typy rozszerzeń projektu. Językiem domyślnym projektu jest C++.

### <a name="create-a-vspackage"></a>Utwórz pakietu VSPackage

1. Utwórz nowy pakietu VSPackage z szablonem projektu pakietu programu Visual Studio.

    Jeśli dodajesz usługę języka do istniejącego pakietu VSPackage, Pomiń poniższe kroki i przejdź bezpośrednio do procedury "Tworzenie klasy usługi językowej".

2. Wprowadź MyLanguagePackage jako nazwę projektu, a następnie kliknij przycisk **OK**.

    Możesz użyć dowolnej nazwy. W tych procedurach opisano założono, że MyLanguagePackage jako nazwę.

3. Wybierz [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] język i opcję, aby wygenerować nowy plik klucza. Kliknij przycisk **Dalej**.

4. Wprowadź odpowiednie informacje o firmie i pakiecie. Kliknij przycisk **Dalej**.

5. Wybierz **polecenie menu**. Kliknij przycisk **Dalej**.

    Jeśli nie planujesz obsługi fragmentów kodu, po prostu kliknij przycisk Zakończ i zignoruj następny krok.

6. Wprowadź **Wstaw fragment kodu** jako **nazwę polecenia** i `cmdidInsertSnippet` dla **identyfikatora polecenia**. Kliknij przycisk **Finish** (Zakończ).

    **Nazwa polecenia** i **Identyfikator polecenia** mogą być takie same, jak na przykład.

### <a name="create-the-language-service-class"></a>Tworzenie klasy usługi językowej

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt MyLanguagePackage, wybierz polecenie **Dodaj**, **odwołanie**, a następnie wybierz przycisk **Dodaj nowe odwołanie** .

2. W oknie dialogowym **Dodaj odwołanie** wybierz pozycję **Microsoft. VisualStudio. Package. LanguageService** na karcie **.NET** , a następnie kliknij przycisk **OK**.

     Należy to zrobić tylko raz dla projektu pakietu językowego.

3. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt pakietu VSPackage i wybierz polecenie **Dodaj**, **Klasa**.

4. Upewnij się, że **Klasa** została wybrana na liście szablony.

5. Wprowadź **MyLanguageService. cs** jako nazwę pliku klasy, a następnie kliknij przycisk **Dodaj**.

     Możesz użyć dowolnej nazwy. Te procedury zostały opisane w tym miejscu `MyLanguageService` jako nazwa.

6. W pliku MyLanguageService. cs Dodaj następujące `using` dyrektywy.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]

7. Zmodyfikuj `MyLanguageService` klasę, aby dziedziczyć z <xref:Microsoft.VisualStudio.Package.LanguageService> klasy:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]

8. Umieść kursor w "LanguageService" i w menu **Edytuj**, **IntelliSense** wybierz opcję **Implementuj klasę abstrakcyjną**. Spowoduje to dodanie minimalnych metod niezbędnych do zaimplementowania klasy usługi językowej.

9. Zaimplementuj metody abstrakcyjne zgodnie z opisem w artykule [implementowanie starszej wersji usługi językowej](../../extensibility/internals/implementing-a-legacy-language-service2.md).

### <a name="register-the-language-service"></a>Rejestrowanie usługi językowej

1. Otwórz plik MyLanguagePackagePackage. cs i Dodaj następujące `using` dyrektywy:

     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]

2. Zarejestruj swoją klasę usługi językowej zgodnie z opisem w temacie [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md). Obejmuje to atrybuty ProvideXX i "proffering usługi językowej". Użyj MyLanguageService, w którym w tym temacie jest używana TestLanguageService.

### <a name="the-parser-and-scanner"></a>Analizator i skaner

1. Zaimplementuj parser i skaner dla Twojego języka zgodnie z opisem w artykule [analizator składni usługi w starszej wersji i skanera](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

     Sposób implementacji parsera i skanera są całkowicie do Ciebie i wykracza poza zakres tego tematu.

## <a name="language-service-features"></a>Funkcje usługi językowej
 Aby zaimplementować każdą funkcję w usłudze językowej, zazwyczaj Klasa pochodzi z odpowiedniej klasy usługi językowej MPF, zaimplementuj wszystkie metody abstrakcyjne w razie potrzeby i Zastąp odpowiednie metody. Klasy tworzone i/lub pochodne są zależne od funkcji, które mają być obsługiwane. Te funkcje zostały szczegółowo omówione w [starszych funkcjach usługi językowej](../../extensibility/internals/legacy-language-service-features1.md). Poniższa procedura jest ogólnym podejściem do wyprowadzania klasy z klas MPF.

#### <a name="deriving-from-an-mpf-class"></a>Wyprowadzanie z klasy MPF

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt pakietu VSPackage i wybierz polecenie **Dodaj**, **Klasa**.

2. Upewnij się, że **Klasa** została wybrana na liście szablony.

     Wprowadź odpowiednią nazwę pliku klasy, a następnie kliknij przycisk **Dodaj**.

3. W nowym pliku klasy Dodaj następujące `using` dyrektywy.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]

4. Zmodyfikuj klasę, aby dziedziczyć z żądanej klasy MPF.

5. Dodaj Konstruktor klasy, który przyjmuje co najmniej te same parametry, co Konstruktor klasy bazowej i przekaż parametry konstruktora do konstruktora klasy bazowej.

     Na przykład Konstruktor klasy pochodzącej od <xref:Microsoft.VisualStudio.Package.Source> klasy może wyglądać następująco:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]

6. W menu **Edytuj**, **IntelliSense** wybierz opcję **Implementuj klasę abstrakcyjną** , jeśli klasa bazowa ma wszystkie metody abstrakcyjne, które muszą być zaimplementowane.

7. W przeciwnym razie Umieść karetkę wewnątrz klasy i wprowadź metodę, która ma zostać zastąpiona.

     Na przykład wpisz, `public override` Aby wyświetlić listę wszystkich metod, które mogą zostać zastąpione w tej klasie.

## <a name="see-also"></a>Zobacz też
- [Implementowanie starszej wersji usługi językowej](../../extensibility/internals/implementing-a-legacy-language-service1.md)
