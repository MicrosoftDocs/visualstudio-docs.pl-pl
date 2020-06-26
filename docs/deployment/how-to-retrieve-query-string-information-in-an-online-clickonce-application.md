---
title: Pobieranie informacji o ciągu zapytania w aplikacji ClickOnce w trybie online
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, query strings
- query strings, retrieving information
ms.assetid: 48ce098a-a075-481b-a5f5-c8ba11f63120
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d0e177f1d41655ffa6fb6b6bbfa52cfc29d15fd6
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382188"
---
# <a name="how-to-retrieve-query-string-information-in-an-online-clickonce-application"></a>Instrukcje: pobieranie informacji o ciągu zapytania w aplikacji ClickOnce w trybie online
*Ciąg zapytania* jest częścią adresu URL zaczynającą się od znaku zapytania (?), który zawiera dowolne informacje w postaci *nazwa = wartość*. Załóżmy, że masz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikację `WindowsApp1` , która jest hostem `servername` , i chcesz przekazać wartość zmiennej `username` podczas uruchamiania aplikacji. Twój adres URL może wyglądać następująco:

 `http://servername/WindowsApp1.application?username=joeuser`

 Poniższe dwie procedury pokazują, jak używać [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji do uzyskiwania informacji o ciągu zapytania.

> [!NOTE]
> Informacje można przekazać tylko w ciągu zapytania, gdy aplikacja jest uruchamiana przy użyciu protokołu HTTP, a nie przy użyciu udziału plików lub lokalnego systemu plików.

 Pierwsza procedura pokazuje, w jaki sposób [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja może używać małego fragmentu kodu do odczytywania tych wartości podczas uruchamiania aplikacji.

 W następnej procedurze pokazano, jak skonfigurować [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikację przy użyciu MageUI.exe, aby można było akceptować parametry ciągu zapytania. Należy to zrobić po każdym opublikowaniu aplikacji.

> [!NOTE]
> Zapoznaj się z sekcją "zabezpieczenia" w dalszej części tego tematu przed podjęciem decyzji o włączeniu tej funkcji.

 Aby uzyskać informacje dotyczące sposobu tworzenia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia przy użyciu *Mage.exe* lub *MageUI.exe*, zobacz [Przewodnik: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

> [!NOTE]
> Począwszy od .NET Framework 3,5 z dodatkiem SP1, możliwe jest przekazanie argumentów wiersza polecenia do aplikacji w trybie offline [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Jeśli chcesz podać argumenty do aplikacji, możesz przekazać parametry do pliku skrótu za pomocą. Rozszerzenie APPREF-MS.

### <a name="to-obtain-query-string-information-from-a-clickonce-application"></a>Aby uzyskać informacje o ciągu zapytania z aplikacji ClickOnce

1. Umieść poniższy kod w projekcie. Aby ten kod działał, trzeba mieć odwołanie do System. Web i Add `using` lub `Imports` dyrektyw for System. Web, system. Collections. specjalizowane i system. Deployment. Application.

     [!code-csharp[ClickOnceQueryString#1](../deployment/codesnippet/CSharp/how-to-retrieve-query-string-information-in-an-online-clickonce-application_1.cs)]
     [!code-vb[ClickOnceQueryString#1](../deployment/codesnippet/VisualBasic/how-to-retrieve-query-string-information-in-an-online-clickonce-application_1.vb)]

2. Wywołaj wcześniej zdefiniowaną funkcję, aby pobrać <xref:System.Collections.DictionaryBase.Dictionary%2A> parametry ciągu zapytania indeksowane według nazwy.

### <a name="to-enable-query-string-passing-in-a-clickonce-application-with-mageuiexe"></a>Aby włączyć przekazywanie ciągu zapytania w aplikacji ClickOnce przy użyciu MageUI.exe

1. Otwórz wiersz polecenia programu .NET i wpisz:

   ```cmd
   MageUI
   ```

2. Z menu **plik** wybierz polecenie **Otwórz**, a następnie otwórz manifest wdrożenia dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, czyli plik kończący się `.application` rozszerzeniem.

3. Wybierz panel **Opcje wdrożenia** w oknie nawigacyjnym po lewej stronie, a następnie zaznacz pole wyboru **Zezwalaj na przekazywanie parametrów adresu URL do aplikacji** .

4. Z menu **plik** wybierz pozycję **Zapisz**.

> [!NOTE]
> Alternatywnie można włączyć przekazywanie ciągu zapytania w [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] . Wybierz pole wyboru **Zezwalaj na przekazywanie parametrów adresu URL do aplikacji** , które można znaleźć, otwierając **właściwości projektu**, wybierając kartę **Publikowanie** , klikając przycisk **Opcje** , a następnie wybierając **manifesty**.

## <a name="robust-programming"></a>Niezawodne programowanie
 W przypadku używania parametrów ciągu zapytania należy zadbać o to, aby Twoja aplikacja została zainstalowana i aktywowana. Jeśli aplikacja jest skonfigurowana do instalacji na komputerze użytkownika z sieci Web lub z udziału sieciowego, prawdopodobnie użytkownik będzie aktywować aplikację tylko raz za pośrednictwem adresu URL. Następnie użytkownik zazwyczaj aktywuje aplikację przy użyciu skrótu w menu **Start** . W związku z tym aplikacja ma gwarancję otrzymywania argumentów ciągu zapytania tylko raz w okresie istnienia. Jeśli zdecydujesz się przechowywać te argumenty na komputerze użytkownika do użytku w przyszłości, użytkownik jest odpowiedzialny za przechowywanie ich w bezpieczny i bezpieczny sposób.

 Jeśli aplikacja działa tylko w trybie online, będzie zawsze aktywowana za pomocą adresu URL. Nawet w takim przypadku aplikacja musi być poprawnie zapisywana, aby działała prawidłowo, jeśli brakuje parametrów ciągu zapytania lub są one uszkodzone.

## <a name="net-framework-security"></a>zabezpieczenia .NET Framework
 Zezwalaj na przekazywanie parametrów adresu URL do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji tylko wtedy, gdy planujesz oczyścić dane wejściowe ze wszystkich złośliwych znaków przed użyciem. Ciąg osadzony z cudzysłowami, ukośnikami lub średnikami może wykonywać dowolne operacje na danych, jeśli użyto niefiltrowanych w zapytaniu SQL z bazą danych. Aby uzyskać więcej informacji na temat zabezpieczeń ciągów zapytań, zobacz [Omówienie luk](https://msdn.microsoft.com/Library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07)w zabezpieczeniach.

## <a name="see-also"></a>Zobacz też
- [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)
