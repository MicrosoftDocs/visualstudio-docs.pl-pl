---
title: Wyświetlanie pamięci dla zmiennych w debugerze | Microsoft Docs
description: Dowiedz się, jak używać systemu Windows w trakcie debugowania, aby zobaczyć miejsce w pamięci używane przez aplikację. Inne okna pokazują zmienne i miejsca, w których znajdują się one w pamięci.
ms.custom: SEO-VS-2020
ms.date: 10/04/2018
ms.topic: how-to
f1_keywords:
- vs.debug.memory
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Memory window
- strings [Visual Studio], viewing
- debugger [Visual Studio], Memory window
- memory [Visual Studio], debugging
- debugging [Visual Studio], Memory window
- buffers, viewing
ms.assetid: 7f7a0439-10e4-4966-bb2d-51f04cda4fe2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0c39024e32c899310b88c1b0583d5b292b063937
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903129"
---
# <a name="use-the-memory-windows-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Korzystanie z okien pamięci w debugerze programu Visual Studio (C#, C++, Visual Basic, F #)

Podczas debugowania, okno **pamięci** pokazuje miejsce w pamięci używane przez aplikację.

Okna debugera, takie jak **Watch**, **autostarty**, zmienne **lokalne** i okno dialogowe **QuickWatch** , umożliwiają wyświetlanie zmiennych, które są przechowywane w określonych lokalizacjach w pamięci. W oknie **pamięci** zostanie wyświetlony obraz ogólny. Widok pamięci jest wygodną metodą badania dużych fragmentów danych (np. buforów lub dużych ciągów), które nie są dobrze wyświetlane w innych oknach.

Okno **pamięci** nie jest ograniczone do wyświetlania danych. Wyświetla wszystko w przestrzeni pamięci, w tym dane, kod i losowe bity elementów bezużytecznych w nieprzydzielonej pamięci.

Okno **pamięci** nie jest dostępne na potrzeby debugowania skryptów i SQL. Te języki nie rozpoznają koncepcji pamięci.

## <a name="open-a-memory-window"></a>Otwórz okno pamięci

Podobnie jak w przypadku innych okien debugera, okna **pamięci** są dostępne tylko podczas sesji debugowania.

>[!IMPORTANT]
>Aby włączyć okna **pamięci** , należy **włączyć debugowanie na poziomie adresu** w   >  **opcjach** narzędzia (lub   >  **Opcje** debugowania) > **debugowanie**  >  **Ogólne**.

**Aby otworzyć okno pamięci**

1. Upewnij się, że opcja **Włącz debugowanie na poziomie adresu** została wybrana w   >  **opcji** narzędzia (lub   >  **Opcje** debugowania) > **debugowanie**  >  **Ogólne**.

1. Rozpocznij debugowanie, wybierając zieloną strzałkę, naciskając klawisz **F5** lub wybierając **Debuguj**  >  **Rozpocznij debugowanie**.

2. W obszarze **Debuguj**  >  **pamięć systemu Windows**  >  wybierz opcję **pamięć 1**, **pamięć 2**, **pamięć 3** lub **pamięć 4**. (Niektóre wersje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oferty oferują tylko jedno okno **pamięci** ).

## <a name="move-around-in-the-memory-window"></a>Poruszanie się w oknie pamięci

Przestrzeń adresowa komputera jest duża i można łatwo stracić miejsce przez przewijanie w oknie **pamięci** .

Wyższe adresy pamięci są wyświetlane u dołu okna. Aby wyświetlić wyższy adres, przewiń w dół. Aby wyświetlić dolny adres, przewiń w górę.

Możesz natychmiast przejść do określonego adresu w oknie **pamięci** za pomocą przeciągania i upuszczania lub wprowadzając adres w polu **adres** . Pole **Address** akceptuje adresy alfanumeryczne i wyrażenia, które obliczają adresy, na przykład `e.User.NonroamableId` .

Aby wymusić natychmiastowe ponowne obliczanie wyrażenia w polu **adres** , wybierz ikonę wyświetlona strzałka **automatycznie przeszacowana** .

Domyślnie okno **pamięci** traktuje wyrażenia **adresów** jako wyrażenia dynamiczne, które są ponowne oceniane podczas uruchamiania aplikacji. Wyrażenia dynamiczne mogą być przydatne, na przykład w celu wyświetlenia pamięci, która jest dotykająca zmiennej wskaźnika.

**Aby przejść do lokalizacji w pamięci, użyj przeciągania i upuszczania:**

1. W dowolnym oknie debugera wybierz adres pamięci lub zmienną wskaźnika, która zawiera adres pamięci.

2. Przeciągnij i upuść adres lub wskaźnik w oknie **pamięci** . Następnie ten adres pojawia się w polu **adres** , a okno **pamięci** dostosowuje się do wyświetlania tego adresu u góry.

**Aby przenieść się do lokalizacji w pamięci, wprowadzając ją w polu adres:**

- Wpisz lub wklej adres lub wyrażenie w polu **adres** , a następnie naciśnij klawisz **Enter** lub wybierz go z listy rozwijanej w polu **adres** . Okno **pamięci** dostosowuje się do wyświetlania tego adresu u góry.

## <a name="customize-the-memory-window"></a>Dostosowywanie okna pamięci

Domyślnie zawartość pamięci jest wyświetlana jako 1-bajtowa liczba całkowita w formacie szesnastkowym, a szerokość okna określa liczbę wyświetlanych kolumn. Możesz dostosować sposób, w jaki okno **pamięci** wyświetla zawartość pamięci.

**Aby zmienić format zawartości pamięci:**

- Kliknij prawym przyciskiem myszy w oknie **pamięć** , a następnie wybierz odpowiednie formaty z menu kontekstowego.

**Aby zmienić liczbę kolumn w oknie pamięci:**

- Wybierz strzałkę listy rozwijanej obok pola **kolumny** , a następnie wybierz liczbę kolumn do wyświetlenia lub wybierz opcję **Automatyczne** dopasowanie na podstawie szerokości okna.

Jeśli nie chcesz, aby zawartość okna **pamięci** była zmieniana podczas uruchamiania aplikacji, możesz wyłączyć ocenianie wyrażeń na żywo.

**Aby włączyć ocenę na żywo:**

- Kliknij prawym przyciskiem myszy w oknie **pamięć** , a następnie w menu kontekstowym wybierz opcję **automatycznie Oceń** .

  >[!NOTE]
  >Obliczenie wyrażenia na żywo jest domyślnie włączone, więc wybranie opcji **Oblicz automatycznie** powoduje wyłączenie. Ponowne wybór zostanie **automatycznie** przywrócone ponownie.

Pasek narzędzi można ukryć lub wyświetlić u góry okna **pamięci** . Nie będziesz mieć dostępu do pola **adres** lub innych narzędzi, gdy pasek narzędzi jest ukryty.

**Aby włączyć wyświetlanie paska narzędzi:**

- Kliknij prawym przyciskiem myszy w oknie **pamięć** , a następnie wybierz polecenie **Pokaż pasek narzędzi** w menu kontekstowym. Pasek narzędzi pojawia się lub znika, w zależności od jego poprzedniego stanu.

## <a name="follow-a-pointer-through-memory"></a>Obserwuj wskaźnik przez pamięć

W aplikacjach kodu natywnego można używać nazw rejestrów jako wyrażeń dynamicznych. Na przykład możesz użyć wskaźnika stosu, aby postępować zgodnie ze stosem.

**Aby obserwować wskaźnik przez pamięć:**

1. W polu **adres** okna **pamięci** wprowadź wyrażenie wskaźnika, które znajduje się w bieżącym zakresie. W zależności od języka może być konieczne jego wypróbowanie.

2.  Naciśnij klawisz **Enter**.

   W przypadku użycia polecenia Debug, takiego jak **Step**, adres pamięci wyświetlany w polu **adres** i w górnej części okna **pamięci** automatycznie zmienia się w miarę zmiany wskaźnika.

## <a name="see-also"></a>Zobacz też
- [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)