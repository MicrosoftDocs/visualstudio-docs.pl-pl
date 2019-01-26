---
title: 'Instrukcje: Pobieranie informacji o ciągu zapytania w aplikacji ClickOnce w trybie Online | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: df24beeb291efde66498e14fc9e95c980e04c553
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55041273"
---
# <a name="how-to-retrieve-query-string-information-in-an-online-clickonce-application"></a>Instrukcje: Pobieranie informacji o ciągu zapytania w aplikacji ClickOnce w trybie online
*Ciągu zapytania* jest to część URL zaczynającym się od znaku zapytania (?), który zawiera dowolne informacje w formie *nazwa = wartość*. Załóżmy, że masz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji o nazwie `WindowsApp1` hostujący na `servername`, i chcesz przekazać wartość zmiennej `username` po uruchomieniu aplikacji. Adres URL może wyglądać następująco:  
  
 `http://servername/WindowsApp1.application?username=joeuser`  
  
 Dwie następujące procedury przedstawiają sposób użycia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, aby uzyskać informacje o parametrach zapytania.  
  
> [!NOTE]
>  Informacje można przekazać w ciągu zapytania tylko, gdy aplikacja jest półtora przy użyciu protokołu HTTP zamiast przy użyciu udziału plików lub lokalnego systemu plików.  
  
 Pierwszy pokazuje procedury jak Twoje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja może użyć niewielkim fragmentem kodu do odczytu tych wartości, po uruchomieniu aplikacji.  
  
 Następna procedura przedstawia sposób konfigurowania usługi [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji przy użyciu MageUI.exe, aby akceptował parametry ciągu zapytania. Należy to zrobić, gdy publikujesz aplikację.  
  
> [!NOTE]
>  Przed wprowadzeniem decyzji, aby włączyć tę funkcję, zobacz sekcję "Zabezpieczenia" w dalszej części tego tematu.  
  
 Aby uzyskać informacje o sposobie tworzenia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożeniu przy użyciu *Mage.exe* lub *MageUI.exe*, zobacz [instruktażu: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
> [!NOTE]
>  Począwszy od programu .NET Framework 3.5 z dodatkiem SP1, istnieje możliwość przekazać argumenty wiersza polecenia do trybu offline [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. Jeśli chcesz podać argumenty do aplikacji, możesz przekazać parametry w pliku skrótu, za pomocą. Rozszerzenie APPREF MS.  
  
### <a name="to-obtain-query-string-information-from-a-clickonce-application"></a>Aby uzyskać informacje o parametrach zapytania z aplikacji ClickOnce  
  
1.  Umieść następujący kod w projekcie. Aby ten kod do funkcji, trzeba będzie zawierać odwołanie do System.Web i Dodaj `using` lub `Imports` instrukcji System.Web, System.Collections.Specialized i System.Deployment.Application.  
  
     [!code-csharp[ClickOnceQueryString#1](../deployment/codesnippet/CSharp/how-to-retrieve-query-string-information-in-an-online-clickonce-application_1.cs)]
     [!code-vb[ClickOnceQueryString#1](../deployment/codesnippet/VisualBasic/how-to-retrieve-query-string-information-in-an-online-clickonce-application_1.vb)]  
  
2.  Wywołaj funkcję zdefiniowany wcześniej w celu pobrania <xref:System.Collections.DictionaryBase.Dictionary%2A> parametrów ciągu zapytania, indeksowane według nazwy.  
  
### <a name="to-enable-query-string-passing-in-a-clickonce-application-with-mageuiexe"></a>Aby włączyć ciągu zapytania w aplikacji ClickOnce za pomocą MageUI.exe  
  
1. Otwórz wiersz polecenia platformy .NET, wpisz:  
  
   ```cmd  
   MageUI  
   ```  
  
2. Z **pliku** menu, wybierz opcję **Otwórz**i otwarcie manifestu wdrażania dla Twojego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikację, która znajduje się plik kończy się rozszerzeniem `.application` rozszerzenia.  
  
3. Wybierz **opcje wdrażania** panelu w oknie nawigacji po lewej stronie, a następnie wybierz **Zezwalaj na adres URL parametry do przekazania do aplikacji** pole wyboru.  
  
4. Z **pliku** menu, wybierz opcję **Zapisz**.  
  
> [!NOTE]
>  Alternatywnie można włączyć ciągu zapytania, przekazując [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Wybierz **Zezwalaj na adres URL parametry do przekazania do aplikacji** pola wyboru, które można znaleźć, otwierając **właściwości projektu**, wybierając opcję **Publikuj** kartę, klikając przycisk **Opcje** przycisk, a następnie wybierając **manifesty**.  
  
## <a name="robust-programming"></a>Skuteczne programowanie  
 Używając parametrów ciągu zapytania, musisz udzielić szczególną uwagę na jak zainstalować i uaktywnić aplikację. Jeśli Twoja aplikacja jest skonfigurowana do zainstalowania na komputerze użytkownika z sieć Web lub udziału sieciowego, istnieje prawdopodobieństwo, że użytkownik będzie aktywowania aplikacji tylko raz za pomocą adresu URL. Po tym, użytkownik będzie zazwyczaj uaktywnić swoją aplikację przy użyciu skrótu w **Start** menu. W rezultacie aplikacja jest gwarantowane otrzymują argumenty ciągu zapytania tylko raz podczas jego okres istnienia. Jeśli chcesz przechowywać tych argumentów na komputerze użytkownika do użytku w przyszłości, ponosisz odpowiedzialność za przechowywanie ich w bezpieczny sposób.  
  
 Jeśli aplikacja jest w trybie online tylko, zawsze będzie ona aktywowana przy użyciu adresu URL. Nawet w takim jednak aplikacji muszą być napisane działała poprawnie, jeśli parametry ciągu zapytania lub są uszkodzone.  
  
## <a name="net-framework-security"></a>zabezpieczenia .NET Framework  
 Zezwalaj na przekazywanie parametrów adresu URL do swojej [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji tylko wtedy, gdy planujesz czyszczenia danych wejściowych złośliwego znaki przed jego użyciem. Ciąg osadzone cudzysłowy, ukośniki lub średnikami, na przykład, mogą wykonywać operacje na danych dowolnego użycie niefiltrowane w zapytaniu SQL względem bazy danych. Aby uzyskać więcej informacji na temat zabezpieczeń ciągu zapytania, zobacz [skrypt wykorzystuje Przegląd](https://msdn.microsoft.com/Library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07).  
  
## <a name="see-also"></a>Zobacz także  
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)