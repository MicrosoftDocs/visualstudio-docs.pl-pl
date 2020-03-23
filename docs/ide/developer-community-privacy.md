---
title: Prywatne dane dla raportów o problemach
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
ms.openlocfilehash: 1e87f35778b8aec615410312c0eb7373d4e9969f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75775896"
---
# <a name="developer-community-data-privacy"></a>Prywatność danych w społeczności deweloperów

Domyślnie wszystkie informacje zawarte w raportach o problemach [w społeczności deweloperów](https://developercommunity.visualstudio.com/), w tym wszelkie komentarze i odpowiedzi, są publicznie widoczne. Jest to korzystne, ponieważ pozwala całej społeczności zobaczyć problemy, rozwiązania i obejścia, które inni użytkownicy znaleźli. Jeśli jednak martwisz się o prywatność swoich danych lub tożsamości, masz opcje.

## <a name="identity-privacy"></a>Prywatność tożsamości

Jeśli obawiasz się ujawnienia swojej tożsamości, [utwórz nowe konto Microsoft,](https://signup.live.com/) które nie ujawnia żadnych szczegółów na Twój temat. Użyj tego konta, aby utworzyć raport.

## <a name="data-privacy"></a>Prywatność danych

Jeśli martwisz się o prywatność danych, nie umieszczaj niczego, co chcesz zachować jako prywatne w tytule lub treści początkowego raportu, który jest zawsze publiczny. Zamiast tego utwórz raport, a następnie zanotuj, że szczegóły będą wysyłane prywatnie w osobnym komentarzu. Po utworzeniu raportu o problemie można określić, kto może wyświetlać odpowiedzi i załączniki:

1. W utworzonym raporcie wybierz pozycję **Dodaj komentarz,** aby utworzyć prywatny opis problemu.

2. W edytorze odpowiedzi użyj formantu poniżej **przycisków Prześlij** i **Anuluj,** aby określić grupę odbiorców odpowiedzi. Wybierz **pozycję Widoczne dla moderatorów i oryginalny plakat,** aby ograniczyć widoczność dla pracowników firmy Microsoft i dla siebie.

   ![Kontrola prywatności w społeczności deweloperów](media/developer-community-privacy-control.png)

   Tylko osoby, które określisz, mogą zobaczyć komentarz oraz wszelkie obrazy, linki lub kod, które w nim znajdziesz. Wszystkie odpowiedzi pod komentarzem mają taką samą widoczność jak oryginalny komentarz. Jest to prawdą, nawet jeśli kontrola prywatności w odpowiedziach nie pokazuje poprawnie stanu ograniczonej widoczności.

3. Dodaj opis i wszelkie inne informacje, obrazy i załączniki plików potrzebne do odtworzenia. Wybierz przycisk **Prześlij,** aby wysłać te informacje prywatnie.

   > [!NOTE]
   > Istnieje limit 2 GB dla załączonych plików i maksymalnie 10 plików. Jeśli chcesz przekazać większy plik, możesz przesłać nowy raport o problemie lub poprosić o przesłanie adresu URL od pracownika firmy Microsoft w komentarzu prywatnym.

Aby zachować prywatność i zachować poufne informacje z widoku publicznego, należy zadbać o to, aby wszystkie interakcje z firmą Microsoft udzielały odpowiedzi w komentarzu z ograniczeniami widoczności. Odpowiedzi na inne komentarze mogą spowodować przypadkowe ujawnienie poufnych informacji.

## <a name="data-we-collect"></a>Dane, które gromadzimy

Jeśli **zgłoś problem** jest inicjowany z Instalatora programu Visual Studio, zbieramy najnowszy dziennik konfiguracji.

Jeśli **zgłoś problem** jest inicjowany z programu Visual Studio, zbieramy co najmniej jeden z następujących typów danych:

- Wpisy programu Watson i platformy .NET z dziennika zdarzeń

- Plik dziennika aktywności programu Visual Studio w pamięci

- Pliki PerfWatson, jeśli kolekcja watsona jest włączona

- Pliki dziennika LiveShare, jeśli istnieją

- Pliki dziennika platformy Xamarin, jeśli istnieją

- Nuget plików dziennika, jeśli istnieją

- Pliki dziennika debugera sieci Web, jeśli istnieją

- Dzienniki usługi Centrum usług i dzienniki błędów MEF, jeśli istnieją

- Dzienniki języka Python, jeśli istnieją

- Dzienniki formularzy systemu Windows, jeśli istnieją

- Zrzut ekranu, jeśli zdecydujesz się go dołączyć

- Rejestrowanie danych, jeśli zdecydujesz się dołączyć nagranie, które obejmuje:

  - Kroki, aby odtworzyć problem

  - Plik śledzenia ETL

  - Plik zrzutu

> [!NOTE]
> Pliki dziennika, zrzuty ekranu i przesyłane dane nagrywające mogą znacznie zwiększyć zdolność firmy Microsoft do zrozumienia problemu i reagowania na nie.  Dlatego zalecamy włączenie ich. Aby chronić prywatność użytkownika, wszystkie załączone pliki dziennika, zrzuty ekranu i dane nagrywania są wysyłane do firmy Microsoft tylko wtedy, gdy użytkownik udziela zgody, przesyłając raport o problemie, z którym są dołączone. Przed przesłaniem raportu możesz sprawdzić, które pliki są zawarte w kroku "Podsumowanie" okna "Zgłoś problem". Możesz wykluczyć pliki dziennika systemowego z raportu, odznaczając "Dołącz dzienniki systemowe" w kroku "Podsumowanie". Aby uzyskać odwołanie, zobacz poniższy zrzut ekranu. 
  > ![Zgłoś problem — podsumowanie zebranych dzienników](media/report-a-problem-logs-collected.png)


## <a name="see-also"></a>Zobacz też

- [Jak zgłosić problem z programem Visual Studio](how-to-report-a-problem-with-visual-studio.md)
- [Prywatność danych o problemach z c++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset#reports-and-privacy)
