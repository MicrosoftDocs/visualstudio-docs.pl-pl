---
title: Program poprawy jakości obsługi klienta
description: Dowiedz się, jak zarządzać ustawieniami prywatności w programie Visual Studio.
ms.date: 05/21/2018
ms.topic: conceptual
author: PoulChapman
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6c7f425d87ba6316c3a3cab66f2b342b4c1141f4
ms.sourcegitcommit: 5c0e20fc6005bc1f8ca38f4122378c4ac21ba89a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2021
ms.locfileid: "106110600"
---
# <a name="visual-studio-customer-experience-improvement-program"></a>Program poprawy jakości obsługi klienta systemu Visual Studio

Program Visual Studio Program poprawy jakości obsługi klienta (VSCEIP) został zaprojektowany, aby pomóc firmie Microsoft w ulepszaniu programu Visual Studio w miarę upływu czasu. Ten program [zbiera informacje o błędach](../ide/diagnostic-data-collection.md), sprzęcie komputerowym i sposobie korzystania przez użytkowników z programu Visual Studio bez zakłócania pracy użytkowników na komputerze. Zbierane informacje ułatwiają firmie Microsoft identyfikację funkcji, które należy poprawić. W tym dokumencie opisano, jak wybrać lub z VSCEIP. W przypadku rezygnacji z **opcjonalnej** kolekcji danych diagnostycznych. Niektóre kolekcje danych diagnostycznych są **wymagane** , aby upewnić się, że program Visual Studio jest bezpieczny, jest aktualny i wykonywany zgodnie z oczekiwaniami. Wybór nie zostanie zmieniony na wymaganą kolekcję danych diagnostycznych.

[!INCLUDE [gdpr-hybrid-note](../misc/includes/gdpr-hybrid-note.md)]
> [!NOTE]
> Ustawienia opt lub out telemetrii VSCEIP nie mają zastosowania do "Zgłoś problem" w programie Visual Studio. Podczas raportowania dzienniki problemów są zbierane i wysyłane do firmy Microsoft tylko w przypadku podania uprawnień przez kliknięcie przycisku Prześlij. Jeśli interesuje Cię zarządzanie dziennikami przed przesłaniem do "Zgłoś problem", zobacz [prywatność danych informacji zwrotnych](./developer-community-privacy.md) , aby uzyskać więcej szczegółów.

## <a name="opt-in-or-out"></a>Zaewidencjonuj lub Wycofaj

VSCEIP jest domyślnie włączona. Można ją wyłączyć lub ponownie włączyć, wykonując następujące instrukcje:

1. W programie Visual Studio wybierz pozycję **Pomoc**  >  **Wyślij opinię**, a następnie wybierz pozycję **Ustawienia**.

   Zostanie otwarte okno dialogowe **program poprawy jakości obsługi programu Visual Studio** .

1. Aby zrezygnować z korzystania z programu, wybierz pozycję **nie, nie chcę uczestniczyć** w programie, a następnie wybierz przycisk **OK**. Wybierz opcję **tak, chcę uczestniczyć**, a następnie wybierz przycisk **OK**.

   ![Okno dialogowe Program poprawy jakości obsługi programu Visual Studio](media/experience-improvement-program.png)

### <a name="registry-settings"></a>Ustawienia rejestru

W przypadku instalowania [narzędzi kompilacji dla programu Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017)należy zaktualizować rejestr w celu skonfigurowania VSCEIP. Klienci korporacyjni mogą utworzyć zasady grupy, aby zrezygnować z VSCEIP lub z nich przez ustawienie zasad opartych na rejestrze.

Odpowiedni klucz rejestru i ustawienia są następujące:

::: moniker range="vs-2017"

- W 64-bitowym systemie operacyjnym, Key = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\15.0\SQM**
- W 32-bitowym systemie operacyjnym, Key = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\15.0\SQM**
- Gdy zasady grupy jest włączona, klucz = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

::: moniker-end

::: moniker range=">=vs-2019"

- W 64-bitowym systemie operacyjnym, Key = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\16.0\SQM**
- W 32-bitowym systemie operacyjnym, Key = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\16.0\SQM**
- Gdy zasady grupy jest włączona, klucz = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

::: moniker-end

Entry = **OptIn powoduje**

Wartość = (DWORD)

- **0** jest wyłączone (Wyłącz VSCEIP)
- **1** jest włączona (Włącz VSCEIP)

> [!CAUTION]
> Niepoprawne edytowanie rejestru może spowodować poważne uszkodzenie systemu. Przed wprowadzeniem zmian w rejestrze należy wykonać kopię zapasową wszystkich cennych danych, które znajdują się na komputerze. W przypadku wystąpienia problemów po zastosowaniu zmian ręcznych można również użyć opcji uruchamiania **Ostatnia znana dobra konfiguracja** .

Aby uzyskać więcej informacji na temat informacji zbieranych, przetwarzanych lub przesyłanych przez VSCEIP, zobacz [zasady zachowania poufności informacji firmy Microsoft](https://privacy.microsoft.com/privacystatement).

## <a name="see-also"></a>Zobacz też

* [Informacje diagnostyczne zebrane przez program Visual Studio](diagnostic-data-collection.md)
* [Opcje opinii programu Visual Studio](../ide/feedback-options.md)
* [Jak zgłosić problem w programie Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md)
* [Społeczność deweloperów programu Visual Studio](https://aka.ms/feedback/suggest?space=8)
* [Oświadczenie o ochronie prywatności w firmie Microsoft](https://privacy.microsoft.com/privacystatement)
