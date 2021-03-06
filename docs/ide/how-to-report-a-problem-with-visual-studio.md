---
title: Jak zgłosić problem w programie Visual Studio
description: Dowiedz się, jak zgłosić problem w programie Visual Studio
ms.date: 03/11/2018
ms.topic: how-to
ms.assetid: bee01179-cde5-4419-9095-190ee0ba5902
author: madskristensen
ms.author: madsk
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 696afd04e5b2fa62fc4f467ea6606b4a9ff0f59e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928084"
---
# <a name="how-to-report-a-problem-with-visual-studio-or-visual-studio-installer"></a>Jak zgłosić problem z programem Visual Studio lub Instalator programu Visual Studio

> [!NOTE]
> Aby uzyskać Visual Studio dla komputerów Mac, zobacz [temat jak zgłosić problem w programie Visual Studio dla komputerów Mac](/visualstudio/mac/report-a-problem).

Możesz zgłosić problem z programu Visual Studio lub jego Instalatora. Wbudowane narzędzie do przesyłania opinii pozwala łatwo dodać informacje diagnostyczne ułatwiające zespołom programu Visual Studio diagnozowanie i rozwiązywanie problemów. Poniżej przedstawiono procedurę zgłaszania problemu.

1. **W programie Visual Studio** wybierz ikonę opinii w prawym górnym rogu, a następnie wybierz pozycję Zgłoś problem. Możesz również uzyskać dostęp do narzędzia opinii z menu **Pomoc** w  >  **wysyłaniu opinii**  >  **Zgłoś problem**.
![Zrzut ekranu przedstawiający ikonę opinii wybraną w prawym górnym rogu okna programu Visual Studio i Zgłoś problem wybrany w menu kontekstowym.](media/feedback-button.png)
Alternatywnie Zgłoś problem w programie **Instalator programu Visual Studio** , jeśli nie możesz zainstalować programu Visual Studio lub nie można uzyskać dostępu do narzędzia opinii w programie Visual Studio.  W instalatorze wybierz ikonę opinii w prawym górnym rogu, a następnie wybierz pozycję Zgłoś problem.
![Zrzut ekranu przedstawiający ikonę opinii wybraną w prawym górnym rogu Instalator programu Visual Studio i Zgłoś problem wybrany w menu kontekstowym.](media/installer.png)

1. Kliknięcie przycisku **Zgłoś problem** spowoduje otwarcie domyślnej przeglądarki i zalogowanie się przy użyciu tego samego konta, którego używasz do logowania się do programu Visual Studio

   ![Zaloguj się, aby zgłosić problem](../ide/media/feedback-browser-top.png)

1. Zacznij od wprowadzenia opisowego tytułu raportu o usterce. Musi składać się z co najmniej 25 znaków.

    ![zgłaszanie problemu](../ide/media/feedback-report.png)

1. Po rozpoczęciu wpisywania w polu Tytuł zostaną wyświetlone możliwe duplikaty.

    ![Wyszukaj duplikaty](../ide/media/feedback-search.png)

1. Wybierz możliwe zduplikowane raporty o usterkach, aby sprawdzić, czy występuje jeden pasujący do własnego problemu. Jeśli jest, zagłosuj na nie, zamiast tworzyć własny bilet.

    ![Zagłosuj na duplikaty](../ide/media/feedback-duplicate.png)

2. Jeśli nie znaleziono żadnych duplikatów, Kontynuuj, wprowadzając opis problemu. Ważne jest, aby być możliwie jasne, aby zwiększyć prawdopodobieństwo odtworzenia usterki przez firmę Microsoft. Upewnij się, że dołączasz jasne kroki odtwarzania.

3. Jeśli jest to istotne dla raportu o usterce, Zrób zrzut ekranu, zaznaczając pole wyboru *Dołącz zrzut ekranu programu Visual Studio* .

    ![Zrób zrzut ekranu ](../ide/media/feedback-screenshot.png) *tylko inżynierowie firmy Microsoft mogą zobaczyć zrzut ekranu*

    Możesz nawet przyciąć zrzut ekranu bezpośrednio w przeglądarce, aby usunąć wszelkie poufne lub niepowiązane części.

4. Najlepszym sposobem, aby pomóc zespołowi inżynieryjnemu programu Visual Studio rozwiązać ten problem, jest udostępnienie śledzenia i plików zrzutu sterty do przeszukania. Można to łatwo zrobić, rejestrując kroki, które spowodowały błąd.

    ![Rejestrowanie akcji ](../ide/media/feedback-recording.png) *tylko inżynierowie firmy Microsoft mogą zobaczyć nagranie*

5. Przejrzyj dołączone pliki i przekaż dodatkowe pliki, jeśli uważasz, że pomoże to zdiagnozować problem.

    ![Dołączone pliki ](../ide/media/feedback-attachments.png) *tylko inżynierowie firmy Microsoft mogą zobaczyć dołączone pliki*

6. Ostatnim krokiem jest naciśnięcie przycisku **Prześlij** . Przesłanie raportu spowoduje jego wysłanie bezpośrednio do wewnętrznego systemu raportowania błędów programu Visual Studio oczekującego na Klasyfikacja.

## <a name="when-further-information-is-needed"></a>Gdy dalsze informacje są zbędne

Gdy w przypadku problemu brakuje ważnych informacji, przypiszemy stan **więcej informacji** . Prosimy o problem z konkretnymi informacjami, których potrzebujemy, i otrzymasz powiadomienie e-mail. Jeśli nie otrzymasz informacji w ciągu siedmiu dni, wyślemy Ci przypomnienie. Po tym czasie będziemy zamykać bilet po 14 dniach braku aktywności.

1. Skorzystaj z linku w wiadomości e-mail do raportu problemu lub przejdź do strony głównej, aby zobaczyć wszystkie raporty w stanie **więcej informacji** .

    ![Zrzut ekranu przedstawiający stronę główną okna Opinie programu Visual Studio. Zostanie wyświetlony jeden element opinii, który jest oznaczony etykietą "Potrzebuję większej ilości informacji" w kolorze czerwonym.](../ide/media/feedback-my-feedback.png)

1. Po wybraniu linku podaj więcej informacji w raporcie o problemie przejdź do nowego ekranu. W tym miejscu możesz zobaczyć, jakie informacje są żądane.

   ![Zrzut ekranu przedstawiający okno opinii programu Visual Studio pokazujący informacje wymagane przez firmę Microsoft w celu rozwiązania problemu.](../ide/media/feedback-need-more-info.png)

1. Więcej informacji można uzyskać, dodając komentarze, załączniki lub kroki nagrywania. To środowisko jest podobne do zgłaszania nowego problemu lub podawania dodatkowych informacji podczas głosowania na temat problemu.

1. Żądanie inżyniera firmy Microsoft otrzymuje powiadomienie o podanych dodatkowych informacjach. Jeśli mają wystarczającą ilość informacji do zbadania, stan problemu ulegnie zmianie. W przeciwnym razie inżynier prosi o podanie jeszcze dalszych informacji.

Te żądania są widoczne na ekranie **moje opinie** , wraz z innymi **problemami** i **sugestiami**.

## <a name="search-for-solutions-or-provide-feedback"></a>Wyszukaj rozwiązania lub Prześlij opinię

Jeśli nie chcesz lub nie możesz użyć programu Visual Studio, aby zgłosić problem, istnieje szansa, że problem został już zgłoszony i rozwiązanie zostało opublikowane na stronie [społeczności deweloperów programu Visual Studio](https://developercommunity2.visualstudio.com/search?space=8) .

Jeśli nie masz problemu z raportowaniem, ale chcesz zasugerować funkcję, istnieje już miejsce. Aby uzyskać więcej informacji, zobacz stronę [Sugeruj funkcję](https://aka.ms/feedback/suggest?space=8) .

## <a name="see-also"></a>Zobacz też

* [Wskazówki dotyczące społeczności deweloperów](./developer-community-guidelines.md)
* [Opcje opinii programu Visual Studio](../ide/feedback-options.md)
* [Zgłoś problem z Visual Studio dla komputerów Mac](/visualstudio/mac/report-a-problem)
* [Zgłoś problem w języku C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Społeczność deweloperów programu Visual Studio](https://aka.ms/feedback/suggest?space=8)
* [Prywatność danych w społeczności deweloperów](developer-community-privacy.md)
