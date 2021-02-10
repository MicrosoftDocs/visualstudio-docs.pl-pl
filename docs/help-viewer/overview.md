---
title: Dokumentacja pomocy w trybie offline
description: Zainstaluj i Wyświetl dokumentację pomocy offline dla różnych produktów i technologii, takich jak Visual Studio i .NET, przy użyciu Podgląd Pomocy firmy Microsoft.
ms.date: 11/02/2017
ms.topic: conceptual
f1_keywords:
- hv_general
helpviewer_keywords:
- Microsoft Help Viewer Help
- Help Viewer, printing a topic
- printing a topic [Help Viewer]
- Help Viewer, toolbar
- Help on Help [Help Viewer]
- Help Viewer, window components
- Help Viewer, navigating
- toolbar [Help Viewer]
ms.assetid: 74e41666-2ce8-4ac0-a0e5-3723d1e322c2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 339d424dd0b09404fc135a119606d47cf7570be3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944098"
---
# <a name="microsoft-help-viewer"></a>Podgląd Pomocy firmy Microsoft

Korzystając z Podgląd Pomocy firmy Microsoft, można zainstalować i wyświetlić zawartość dla różnych produktów i technologii na komputerze lokalnym. Do tych produktów należą Visual Studio, .NET, Dokumentacja języka, SQL Server i programowanie dla systemu Windows. Podgląd pomocy umożliwia wykonywanie:

- Pobierz zestawy zawartości, które są również nazywane książkami. Może to być przydatne, jeśli musisz działać "offline" i nadal mieć dostęp do dokumentacji.

- Znajdź tematy według tytułów, przeglądając i przeszukując Spis treści.

- Wyszukiwanie tematów w indeksie.

- Znajdź informacje przy użyciu wyszukiwania pełnotekstowego.

- Wyświetlanie, zakładanie i drukowanie tematów.

Aby zainstalować podgląd pomocy, zobacz [Podgląd pomocy firmy Microsoft Installation](../help-viewer/installation.md). Aby rozpocząć odczytywanie tematów pomocy w podglądzie pomocy, a nie w trybie online, przejdź do menu **Pomoc** w programie Visual Studio, a następnie wybierz pozycję Ustaw opcję Uruchom **preferencję pomocy**  >  **w podglądzie pomocy**.

> [!TIP]
> Inny sposób na pobranie zawartości lokalnie, aby można było ją wyświetlić, gdy nie masz połączenia z Internetem, aby pobrać wersję pliku PDF. Wiele zestawów dokumentacji na docs.microsoft.com zawierają link w dolnej części spisu treści (TOC) w celu pobrania pliku PDF zawierającego wszystkie artykuły dla tego spisu treści.
>
> ![Pobierz plik PDF dla dokumentacji programu Visual Studio](media/overview/download-pdf.png)

## <a name="help-viewer-tour"></a>Przewodnik po przeglądarce pomocy

Informacje w zainstalowanej zawartości można znaleźć, korzystając z kart nawigacyjnych, wyświetlić zainstalowaną zawartość na karcie tematu lub kartach i zarządzać zawartością przy użyciu karty **Zarządzanie zawartością** . Możesz również wykonywać dodatkowe zadania za pomocą przycisków na pasku narzędzi i znaleźć dodatkowe informacje w prawym dolnym rogu okna.

### <a name="navigation-tabs"></a>Karty nawigacji

|Tab|Opis|
|---|-----------|
|Zawartość|Wyświetla zainstalowaną zawartość jako hierarchię (spis treści). Możesz określić kryteria filtrowania wyświetlanych tytułów.|
|Indeks|Wyświetla alfabetyczną listę indeksowanych terminów. Można wyszukać indeks, określić kryteria filtrowania wpisów i wymagać, aby wpisy indeksu zawierały lub rozpoczynać się od określonego tekstu.|
|Ulubione|Aby uzyskać informacje na temat ulubionych, wybierz przycisk **Dodaj do ulubionych** , a na tej karcie są wyświetlane tematy. Sekcja **historia** zawiera listę tematów, które były ostatnio oglądane.|
|Wyszukaj|Zawiera pole tekstowe, w którym można wyszukać warunki w dowolnym miejscu zawartości, w tym o tytułach kodu i tematu.|

### <a name="view-topics"></a>Wyświetl tematy

Każdy temat pojawia się na własnej karcie i można otworzyć wiele tematów w tym samym czasie.

### <a name="manage-content"></a>Zarządzanie zawartością

Można instalować, aktualizować, przenosić i usuwać zawartość za pomocą karty **Zarządzanie zawartością** . W górnej części karty można użyć kontroli **źródła instalacji** , aby określić, czy mają być instalowane książki z lokalizacji sieciowej, czy z dysku lub identyfikatora URI. Pole **ścieżka do magazynu lokalnego** pokazuje, gdzie są zainstalowane książki na komputerze lokalnym, a następnie można przenieść je do innej lokalizacji, wybierając przycisk **Przenieś** .

Lista zawartości zawiera informacje o książkach, które można zainstalować lub których instalacja została już zainstalowana, o tym, czy jest dostępna aktualizacja oraz jak duże są poszczególne książki. Możesz zainstalować lub usunąć jedną lub więcej książek, wybierając odpowiednie **Dodaj** lub **Usuń** linki, a następnie wybierając przycisk **Aktualizuj** w okienku **oczekujące zmiany** . Jeśli aktualizacje są dostępne dla dowolnych książek, które zostały już zainstalowane, możesz odświeżyć tę zawartość, wybierając link **kliknij tutaj, aby pobrać teraz** w dolnej części okna. Ponadto wszystkie zainstalowane książki są odświeżane, jeśli aktualizacje są dostępne podczas instalacji dodatkowych książek.

> [!NOTE]
> Funkcje karty **Zarządzanie zawartością** mogą się różnić, jeśli administrator podglądu pomocy dezaktywuje te funkcje lub jeśli nie jest dostępny żaden dostęp do Internetu.

### <a name="toolbar-buttons"></a>Przyciski paska narzędzi

Pasek narzędzi w oknie **podglądu pomocy** zawiera następujące przyciski:

- Przycisk **Pokaż temat w spisie treści** pokazuje lokalizację tematu na karcie **zawartość** .

- Przycisk **Dodaj do ulubionych** dodaje aktywny temat do karty **Ulubione** .

- Przycisk **Znajdź w temacie** wyróżnia tekst wyszukiwania w aktywnym temacie.

- Przycisk **Drukuj** drukuje lub pokazuje podgląd aktywnego tematu.

- Przycisk **Opcje podglądu** wyświetla ustawienia, takie jak rozmiar wyświetlanego tekstu, liczba wyników wyszukiwania do zwrócenia, liczba tematów pokazywanych w historii i sprawdzanie dostępności aktualizacji w trybie online.

- Przycisk **Zarządzaj zawartością** powoduje, że aktywna jest karta **Zarządzanie zawartością** .

- Niewielki trójkąt po prawej stronie otwiera listę kart, w tym karty tematów i kartę **Zarządzaj zawartością** . Możesz wybrać nazwę karty, aby ją uaktywnić.

## <a name="see-also"></a>Zobacz też

- [Instalacja Podgląd Pomocy firmy Microsoft](../help-viewer/installation.md)
- [Podręcznik administratora podglądu pomocy](../help-viewer/administrator-guide.md)
- [Instalowanie zawartości lokalnej i zarządzanie nią](../help-viewer/install-manage-local-content.md)
