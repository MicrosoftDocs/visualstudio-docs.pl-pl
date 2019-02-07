---
title: Program poprawy jakości obsługi klienta
description: Dowiedz się, jak do zarządzania ustawieniami ochrony prywatności w programie Visual Studio.
ms.date: 05/21/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: PoulChapman
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 96ddafa340f0d9ab87b359cf1a5cc5b92ea7cabe
ms.sourcegitcommit: 01334abf36d7e0774329050d34b3a819979c95a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55852676"
---
# <a name="visual-studio-customer-experience-improvement-program"></a>Program poprawy jakości obsługi klienta programu Visual Studio

Visual Studio klienta środowiska Improvement Program (VSCEIP) zaprojektowano w celu pomóc firmie Microsoft w ulepszaniu programu Visual Studio wraz z upływem czasu. Ten program [zbiera informacje o błędach](../ide/diagnostic-data-collection.md), sprzęt komputerowy i jak użytkownicy korzystają programu Visual Studio, bez zakłócania pracy użytkowników w ich zadań na komputerze. Informacje zbierane pomaga firma Microsoft może identyfikować, które funkcje, aby poprawić. W tym dokumencie opisano sposób korzystania z opcji w lub poza nią VSCEIP.

[!INCLUDE [gdpr-hybrid-note](../misc/includes/gdpr-hybrid-note.md)]

## <a name="opt-in-or-out"></a>Zoptymalizowany pod kątem wewnątrz lub na zewnątrz

VSCEIP jest domyślnie włączona. Można ją wyłączyć lub ponowne zalogowanie, wykonując następujące instrukcje:

1. Uruchom program Visual Studio.

1. Z **pomocy** menu wskaż **Wyślij opinię**, a następnie wybierz pozycję **ustawienia**.

   **Visual Studio Experience Improvement Program** zostanie otwarte okno dialogowe.

1. Aby zrezygnować, należy wybrać **nie, nie chcę uczestniczyć**, a następnie wybierz pozycję **OK**.
   Aby włączyć, wybierz pozycję **tak, chcę uczestniczyć**, a następnie wybierz pozycję **OK**.

   ![Visual Studio Experience Improvement Program okna dialogowego](media/experience-improvement-program.png)

### <a name="registry-settings"></a>Ustawienia rejestru

Jeśli zainstalujesz [Build Tools for Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017), należy zaktualizować rejestru w celu skonfigurowania VSCEIP. Klienci korporacyjni można konstruować zasady grupy chęć uczestnictwa w lub poza nią VSCEIP, ustawiając zasady związane z rejestrem.

Odpowiedni klucz rejestru i ustawienia są następujące:

W 64-bitowych systemach operacyjnych, klucza = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\15.0\SQM** na 32-bitowych systemach operacyjnych, klucza = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\15.0\SQM** zasad grupy po jest włączone, klucz = **HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\VisualStudio\SQM**

Wpis = **OptIn**

Wartość = (DWORD)
- **0** jest wyłączony (Wyłącz VSCEIP)
- **1** jest zgoda (Włącz VSCEIP)

> [!CAUTION]
> Niepoprawne edytowanie rejestru może spowodować poważne uszkodzenie systemu. Przed wprowadzeniem zmian w rejestrze należy wykonać kopię zapasową wszystkich cennych danych, które znajdują się na komputerze. Można również użyć **Ostatnia znana dobra konfiguracja** opcji uruchamiania w razie wystąpienia problemów po zastosowaniu zmiany ręcznie.

Aby uzyskać więcej informacji na temat informacji zbieranych, przetwarzanych lub przekazywanych w ramach VSCEIP, zobacz [zasady zachowania poufności informacji firmy Microsoft](https://privacy.microsoft.com/privacystatement).

## <a name="see-also"></a>Zobacz także

* [Informacje diagnostyczne zebrane przez program Visual Studio](diagnostic-data-collection.md)
* [Porozmawiaj z nami](../ide/talk-to-us.md)
* [Jak zgłosić problem z programem Visual Studio](../ide/how-to-report-a-problem-with-visual-studio-2017.md)
* [Visual Studio Developer Community](https://developercommunity.visualstudio.com/)
* [Poufności informacji firmy Microsoft](https://privacy.microsoft.com/privacystatement)
