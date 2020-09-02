---
title: 'Instrukcje: debugowanie za pomocą programu Code Center Premium Source | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64783475"
---
# <a name="how-to-debug-with-code-center-premium-source"></a>Porady: debugowanie przy użyciu źródła Code Center Premium
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] debugera można debugować bezpieczne udostępnione źródło z centrum kodu Microsoft MSDN w wersji Premium.  
  
 W tym temacie wyjaśniono, jak skonfigurować i debugować kod źródłowy programu Code Center w programie Visual Studio.  
  
### <a name="to-prepare-for-debugging-with-code-center-premium"></a>Aby przygotować się do debugowania za pomocą programu Code Center Premium  
  
1. Podłącz czytnik karty inteligentnej i Wstaw kartę uzyskaną z inicjatywy udostępnionego źródła.  
  
2. Uruchom program Visual Studio.  
  
3. W menu **Tools** (Narzędzia) kliknij pozycję **Options** (Opcje).  
  
4. W oknie dialogowym **Opcje** Otwórz węzeł **debugowanie** , a następnie kliknij pozycję **Ogólne**.  
  
5. Wyczyść pole wyboru **włącz tylko mój kod (tylko zarządzane)** .  
  
6. Wybierz pozycję **Włącz obsługę serwera źródłowego**.  
  
7. Wyczyść pole **Wymagaj, aby pliki źródłowe były dokładnie zgodne z wersją oryginalną**.  
  
8. W węźle **debugowanie** kliknij pozycję **symbole**.  
  
9. W polu **lokalizacje pliku symboli (. pdb)** Usuń zaznaczenie pola wyboru **symbole serwera Microsoft** i Dodaj następujące lokalizacje:  
  
     `https://codepremium.msdn.microsoft.com/symbols`  
  
     `src=https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   > Upewnij się, że na końcu ścieżki zostanie umieszczony końcowy ukośnik <strong>/</strong> .  
  
     Przenieś te lokalizacje na początku listy, aby upewnić się, że te symbole są ładowane jako pierwsze.  
  
   > [!NOTE]
   > Te lokalizacje Premium centrum kodu muszą być wymienione na początku, aby były to pierwsze załadowane lokalizacje. W programie Visual Studio 2010 nie można przenieść żadnych serwerów powyżej pozycji **serwery symboli Microsoft** , co oznacza, że należy wyczyścić pole wyboru.  
   > 
   >  Aby załadować symbole z symboli firmy Microsoft podczas sesji debugowania, wykonaj następujące czynności:  
   > 
   > 1. W menu **debugowanie** wybierz pozycję **Windows** , a następnie wybierz pozycję **moduły**.  
   >    2.  Wybierz moduł, dla którego chcesz utworzyć symbole, a następnie otwórz menu skrótów. Wybierz pozycję **Załaduj symbole z** , a następnie wybierz pozycję **serwery symboli firmy Microsoft**.  
  
10. W polu **symbole pamięci podręcznej z serwerów symboli w tym katalogu** wprowadź lokalizację, na przykład w `C:\symbols` przypadku, gdy usługa Code Center Premium może buforować symbole. Symbole buforowania mogą znacząco poprawić wydajność podczas debugowania.  
  
     Jeśli wystąpią problemy z debugowaniem kodu źródłowego za pomocą programu po wykonaniu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tej procedury, należy sprawdzić lokalizację pamięci podręcznej dla wcześniej buforowanych i nieaktualnych plików symboli. Usuń nieaktualne pliki symboli.  
  
11. Kliknij przycisk **OK**.  
  
12. Uruchom ponownie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , aby upewnić się, że ustawienia są utrwalane.  
  
### <a name="to-debug-your-source-code-using-attach-to-process"></a>Aby debugować kod źródłowy przy użyciu dołączania do procesu  
  
1. Podłącz czytnik karty inteligentnej i Wstaw kartę uzyskaną z inicjatywy udostępnionego źródła.  
  
2. Uruchom program Visual Studio.  
  
3. Otwórz projekt programu Visual Studio.  
  
4. W menu **Narzędzia** kliknij polecenie **Dołącz do procesu**.  
  
5. W oknie dialogowym **Dołącz do procesu** kliknij pozycję **Wybierz**.  
  
6. W oknie dialogowym **Wybieranie typu kodu** w obszarze **Wykryj te typy kodu**wybierz opcję **natywne**, **zarządzane**i **zarządzane (v 4.0)**.  
  
7. Kliknij przycisk **OK** , aby odrzucić okno dialogowe **Wybieranie typu kodu** .  
  
8. W polu **dostępne procesy** wybierz proces, który chcesz debugować.  
  
9. Kliknij przycisk **Dołącz**.  
  
10. Po wyświetleniu monitu o potwierdzenie certyfikatu kliknij przycisk **OK**. Następnie wprowadź numer PIN. Jeśli zostanie wyświetlony monit, zaakceptuj warunki użytkowania usługi Code Center w warstwie Premium.  
  
     Pobieranie symboli może zająć dużo czasu, w zależności od szybkości sieci. Pasek stanu wskazuje, kiedy wszystkie symbole zostały pobrane pomyślnie.  
  
11. Powtórz kroki dołączania dla wszystkich projektów zarządzanych w rozwiązaniu.  
  
### <a name="to-debug-source-code-from-an-existing-solution"></a>Aby debugować kod źródłowy z istniejącego rozwiązania  
  
1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla rozwiązania, a następnie wybierz polecenie **Właściwości**.  
  
2. W oknie dialogowym strony właściwości rozwiązania wybierz pozycję **Debuguj pliki źródłowe** w węźle **wspólne właściwości** .  
  
3. Dodaj następującą lokalizację do **katalogów zawierających pliki źródłowe** :  
  
    `https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   > Upewnij się, że na końcu ścieżki zostanie umieszczony końcowy ukośnik <strong>/</strong> .  
  
4. Dla każdego zarządzanego projektu w rozwiązaniu wykonaj następujące czynności:  
  
   1. W Eksplorator rozwiązań otwórz menu skrótów dla projektu, a następnie wybierz polecenie **Właściwości**.  
  
   2. Wybierz pozycję **Debuguj** , a następnie wybierz pozycję **Włącz debugowanie kodu niezarządzanego**.  
  
### <a name="to-debug-your-solution-with-code-center-premium-source"></a>Aby debugować rozwiązanie przy użyciu programu Code Center Premium Source  
  
1. W `Package` klasie należy ustawić punkt przerwania w konstruktorze pakietu.  
  
2. W `Debug` menu kliknij **Rozpocznij debugowanie**.  
  
3. Po trafieniu punktu przerwania w konstruktorze pakietów przejdź do okna **stosu wywołań** i kliknij prawym przyciskiem myszy ramkę stosu zestawu, z którego mają zostać załadowane symbole, a następnie kliknij pozycję **Załaduj symbole**.  
  
     Kliknij dwukrotnie ramkę wywołania, aby załadować źródło.  
  
### <a name="to-browse-source-code-on-code-center-premium"></a>Aby przeglądać kod źródłowy w centrum kodu Premium  
  
1. Podłącz czytnik karty inteligentnej i Wstaw kartę uzyskaną z inicjatywy udostępnionego źródła.  
  
2. Uruchom program Internet Explorer wprowadź następujący adres URL: `https://codepremium.msdn.microsoft.com`  
  
3. Przeglądaj w celu znalezienia żądanego źródła.  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Centrum kodu — wersja Premium](https://www.microsoft.com/en-us/sharedsource/code-center-premium.aspx)
