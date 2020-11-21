---
title: Dane prywatne dla raportów o problemach
description: Dowiedz się, jak zabezpieczać dane prywatne po utworzeniu raportów o problemach przeznaczonych dla społeczności deweloperów do przejrzenia.
ms.custom: SEO-VS-2020
ms.date: 06/21/2018
ms.topic: conceptual
helpviewer_keywords:
- developer community privacy
- privacy, developer community
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82c89f2f6ec2a1a9bc6c87a600c355226b2f3da4
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2020
ms.locfileid: "95005941"
---
# <a name="developer-community-data-privacy"></a>Prywatność danych w społeczności deweloperów

Domyślnie wszystkie informacje w raportach o problemach w [społeczności deweloperów](https://developercommunity.visualstudio.com/), w tym wszelkie komentarze i odpowiedzi, są widoczne publicznie. Jest to korzystne, ponieważ umożliwia całej społeczności przeglądanie problemów, rozwiązań i obejściów znalezionych przez innych użytkowników. Jeśli jednak obawiasz się o prywatność danych lub tożsamości, możesz korzystać z opcji.

## <a name="identity-privacy"></a>Prywatność tożsamości

Jeśli chodzi o ujawnienie tożsamości, [Utwórz nową konto Microsoft](https://signup.live.com/) , która nie ujawnia żadnych szczegółowych informacji o użytkowniku. Użyj tego konta, aby utworzyć raport.

## <a name="data-privacy"></a>Prywatność danych

Jeśli obawiasz się o prywatność danych, nie umieszczaj żadnych elementów, które chcesz zachować prywatną w tytule lub treści raportu początkowego, który jest zawsze publiczny. Zamiast tego Utwórz raport, a następnie Zwróć uwagę, że dane zostaną wysłane prywatnie w osobnym komentarzu. Po utworzeniu raportu o problemie możesz określić, kto może wyświetlać odpowiedzi i załączniki:

1. W utworzonym raporcie wybierz pozycję **Dodaj komentarz** , aby utworzyć prywatny opis problemu.

2. W edytorze odpowiedzi użyj kontrolki poniżej przycisków **Prześlij** i **Anuluj** , aby określić odbiorców odpowiedzi. Wybierz opcję **widoczne dla moderatorów i oryginalny plakat** , aby ograniczyć widoczność do pracowników firmy Microsoft i siebie.

   ![Kontrola prywatności w społeczności deweloperów](media/developer-community-privacy-control.png)

   Tylko określone osoby mogą zobaczyć komentarz i wszystkie obrazy, linki lub kod, które zawiera. Wszystkie odpowiedzi w komentarzu mają taki sam wgląd jak oryginalny komentarz. Jest to prawdziwe, nawet jeśli kontrola prywatności na odpowiedzi nie pokazuje poprawnie stanu widoczności z ograniczeniami.

3. Dodaj opis i wszelkie inne informacje, obrazy i załączniki plików potrzebne do Odtwórz. Wybierz przycisk **Prześlij** , aby wysłać te informacje prywatnie.

   > [!NOTE]
   > W witrynie sieci Web społeczności deweloperów istnieje limit 2 GB dla dołączonych plików i maksymalnie 10 plików. Jeśli musisz przekazać większy plik, możesz przesłać nowy raport o problemie lub zażądać adresu URL przekazywania od pracownika firmy Microsoft w komentarzu prywatnym.
   > Po zamknięciu problemu skojarzone załączniki zostaną usunięte po 90 dniach.

Aby zachować prywatność i zachować poufne informacje z widoku publicznego, należy zachować ostrożność, aby wszystkie interakcje z firmą Microsoft były odpowiedzią w ramach komentarza z ograniczeniami. Odpowiedzi na inne komentarze mogą spowodować przypadkowe ujawnienie poufnych informacji.

## <a name="data-we-collect"></a>Zbierane dane

Jeśli zainicjujesz **problem** z Instalator programu Visual Studio, zbierzemy najnowszy dziennik instalacji.

Jeśli **Zgłoś problem** w programie Visual Studio, zbieramy co najmniej jeden z następujących typów danych:

- Wpisy programu Watson i .NET z dziennika zdarzeń

- Plik dziennika aktywności w pamięci programu Visual Studio

- Pliki PerfWatson, jeśli jest włączona kolekcja programu Watson

- Pliki dziennika LiveShare (jeśli istnieją)

- Pliki dziennika Xamarin, jeśli istnieją

- Pliki dziennika NuGet, jeśli istnieją

- Pliki dziennika debugera sieci Web, jeśli istnieją

- Dzienniki centrum usług i dzienniki błędów MEF, jeśli istnieją

- Dzienniki języka Python, jeśli istnieją

- Dzienniki edytora LSP (Razor), jeśli istnieją

- Dzienniki Windows Forms, jeśli istnieją

- Zrzut ekranu, jeśli wybierzesz go uwzględnić

- Rejestrowanie danych, jeśli zdecydujesz się na dołączenie nagrania, które obejmuje:

  - Kroki prowadzące do odtworzenia problemu

  - Plik śledzenia ETL

  - Plik zrzutu

> [!NOTE]
> Pliki dziennika, zrzuty ekranu i nagrania przesyłane dane mogą znacząco zwiększyć czytelność firmy Microsoft i reagować na nie.  Zalecamy uwzględnienie ich. Aby chronić prywatność, wszelkie dołączone pliki dziennika, zrzuty ekranu i dane rejestrowania są wysyłane do firmy Microsoft tylko wtedy, gdy podajesz uprawnienia, przesyłając raport o problemie, za pomocą którego zostały uwzględnione. Przed przesłaniem raportu można zobaczyć, które pliki są zawarte w kroku "Podsumowanie" okna "Zgłoś problem". Pliki dziennika systemowego można wykluczać z raportu, usuwając zaznaczenie pola wyboru Dołącz dzienniki systemowe w kroku "Podsumowanie". Aby uzyskać informacje na ten temat, zobacz poniższy zrzut ekranu. 
  > ![Zgłoś problem — podsumowanie zebranych dzienników](media/report-a-problem-logs-collected.png)


## <a name="see-also"></a>Zobacz także

- [Jak zgłosić problem w programie Visual Studio](how-to-report-a-problem-with-visual-studio.md)
- [Prywatność danych raportu o problemach C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset#reports-and-privacy)
