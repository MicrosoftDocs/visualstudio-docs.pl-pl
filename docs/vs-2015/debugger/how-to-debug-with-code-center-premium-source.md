---
title: 'Instrukcje: Debugowanie przy użyciu źródła Code Center Premium | Dokumentacja firmy Microsoft'
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
- Code Center Premium
- debugging [Visual Studio], Code Center Premium
ms.assetid: 18b4769d-b007-4428-9dae-9e72c283ff0d
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db9a3e08e14e7fadca6df9e32361c0b042f565e9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438334"
---
# <a name="how-to-debug-with-code-center-premium-source"></a>Instrukcje: Debugowanie przy użyciu źródła Code Center Premium
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] debugera, możesz przeprowadzić debugowanie bezpiecznego źródłowy udostępniony z Microsoft MSDN Code Center Premium.  
  
 W tym temacie opisano sposób konfigurowania i debugowania kodu źródła Code Center Premium w programie Visual Studio.  
  
### <a name="to-prepare-for-debugging-with-code-center-premium"></a>Aby przygotować się do debugowania za pomocą Code Center Premium  
  
1. Połącz czytnika kart inteligentnych i Wstaw karty, która pochodzi z Shared Source Initiative.  
  
2. Uruchom program Visual Studio.  
  
3. Na **narzędzia** menu, kliknij przycisk **opcje**.  
  
4. W **opcje** po otwarciu okna dialogowego **debugowanie** węzła i kliknij przycisk **ogólne**.  
  
5. Wyczyść **Włącz tylko mój kod (tylko zarządzany)** pole wyboru.  
  
6. Wybierz **Włącz obsługę serwera źródłowego**.  
  
7. Wyczyść **wymaga plików źródłowych Aby dokładnie dopasować oryginalną wersję**.  
  
8. W obszarze **debugowanie** węzła, kliknij przycisk **symbole**.  
  
9. W **pliku symboli (.pdb) lokalizacje** zaznaczenie pola wyboru **symboli serwera Microsoft** pole wyboru, a następnie dodaj następujące lokalizacje:  
  
     `https://codepremium.msdn.microsoft.com/symbols`  
  
     `src=https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   > Pamiętaj dołączyć końcowy ukośnik<strong>/</strong> na końcu ścieżki.  
  
     Przenieś te lokalizacje na początku listy, aby upewnić się, że te symbole są najpierw ładowane.  
  
   > [!NOTE]
   > Te lokalizacje Code Center Premium musi być wymienione jako pierwsze, aby były pierwszy lokalizacje, które są ładowane. W programie Visual Studio 2010 nie można przenieść wszystkie serwery powyżej **serwery symboli firmy Microsoft** zapisu, dlatego należy wyczyścić pole wyboru.  
   > 
   >  Aby załadować symbole z symboli firmy Microsoft podczas sesji debugowania, wykonaj następujące czynności:  
   > 
   > 1. Na **debugowania** menu, wybierz **Windows** , a następnie wybierz **modułów**.  
   >    2.  Wybierz moduł, który ma symbole, a następnie otwórz menu skrótów. Wybierz **Załaduj symbole z** , a następnie wybierz **serwery symboli firmy Microsoft**.  
  
10. W **Buforuj symbole z serwerów symboli w tym katalogu** wprowadź lokalizację, taką jak `C:\symbols` gdzie Code Center Premium może buforować symboli. Pamięć podręczna symboli może znacznie poprawić wydajność podczas debugowania.  
  
     Jeśli wystąpią problemy z debugowania kodu źródłowego za pomocą [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] po ukończeniu tej procedury Sprawdź swoją lokalizację pamięci podręcznej, aby pliki symboli wcześniej pamięci podręcznej i przestarzałe. Usuń pliki symboli nieaktualne.  
  
11. Kliknij przycisk **OK**.  
  
12. Uruchom ponownie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] aby upewnić się, że ustawienia są zachowywane.  
  
### <a name="to-debug-your-source-code-using-attach-to-process"></a>Debugowanie kodu źródłowego za pomocą Dołącz do procesu  
  
1. Połącz czytnika kart inteligentnych i Wstaw karty, która pochodzi z Shared Source Initiative.  
  
2. Uruchom program Visual Studio.  
  
3. Otwórz swój projekt programu Visual Studio.  
  
4. Na **narzędzia** menu, kliknij przycisk **dołączyć do procesu**.  
  
5. W **dołączyć do procesu** okno dialogowe, kliknij przycisk **wybierz**.  
  
6. W **Wybieranie typu kodu** okno dialogowe, w obszarze **wykryć tych typów kodu**, wybierz opcję **natywnych**, **zarządzane**, i **zarządzane ( w wersji 4.0)**.  
  
7. Kliknij przycisk **OK** odrzucać **Wybieranie typu kodu** okno dialogowe.  
  
8. W **dostępne procesy** wybierz proces, który chcesz debugować.  
  
9. Kliknij przycisk **dołączyć**.  
  
10. Po wyświetleniu monitu, aby potwierdzić swój certyfikat, kliknij przycisk **OK**. Następnie wprowadź numer PIN. Po wyświetleniu monitu, należy zaakceptować warunki użytkowania usługi Code Center Premium.  
  
     Pobieranie symboli może potrwać bardzo długo w zależności od szybkości sieci. Na pasku stanu będzie wskazywać, kiedy wszystkie symbole zostały pomyślnie pobrane.  
  
11. Powtórz kroki dołączania dla wszystkich zarządzanych projektów w rozwiązaniu.  
  
### <a name="to-debug-source-code-from-an-existing-solution"></a>Aby debugować kod źródłowy z istniejącego rozwiązania  
  
1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla rozwiązania, a następnie wybierz **właściwości**.  
  
2. W oknie dialogowym strony właściwości rozwiązania wybierz **Debuguj pliki źródłowe** w **wspólne właściwości** węzła.  
  
3. Dodawanie następującej lokalizacji w celu **katalogi zawierające pliki źródłowe** listy:  
  
    `https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   > Pamiętaj dołączyć końcowy ukośnik<strong>/</strong> na końcu ścieżki.  
  
4. Dla każdego zarządzanego projektu w rozwiązaniu wykonaj następujące czynności  
  
   1. W Eksploratorze rozwiązań Otwórz menu skrótów dla projektu, a następnie wybierz **właściwości**.  
  
   2. Wybierz **debugowania** , a następnie wybierz **Włącz debugowanie kodu unmanged**.  
  
### <a name="to-debug-your-solution-with-code-center-premium-source"></a>Aby debugować swoje rozwiązanie przy użyciu źródła Code Center Premium  
  
1. W swojej `Package` klasy, należy ustawić punkt przerwania w Konstruktorze pakietu.  
  
2. W `Debug` menu, kliknij przycisk **Rozpocznij debugowanie**.  
  
3. Po osiągnięciu punktu przerwania w Konstruktorze pakietu przejdź do **stos wywołań** oknie i kliknij prawym przyciskiem myszy ramkę stosu zestawu, który chcesz załadować symbole, następnie kliknij przycisk **załadować symbole**.  
  
     Kliknij dwukrotnie ramki wywołań, aby załadować źródła.  
  
### <a name="to-browse-source-code-on-code-center-premium"></a>Aby przeglądać kod źródłowy w Code Center Premium  
  
1. Połącz czytnika kart inteligentnych i Wstaw karty, która pochodzi z Shared Source Initiative.  
  
2. Uruchomienie Internet Explorer wprowadź następujący adres URL: `https://codepremium.msdn.microsoft.com`  
  
3. Wyszukaj żądane źródło.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Code Center Premium](https://www.microsoft.com/en-us/sharedsource/code-center-premium.aspx)
