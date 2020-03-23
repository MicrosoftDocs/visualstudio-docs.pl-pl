---
title: Program poprawy jakości obsługi klienta
description: Dowiedz się, jak zarządzać ustawieniami prywatności w programie Visual Studio.
ms.date: 05/21/2018
ms.topic: conceptual
author: PoulChapman
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b6c785b755b64f0dd7e367a01d9c05c1981ea558
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "71693014"
---
# <a name="visual-studio-customer-experience-improvement-program"></a>Program poprawy jakości obsługi klienta systemu Visual Studio

Program poprawy jakości obsługi klienta programu Visual Studio (VSCEIP) został zaprojektowany, aby pomóc firmie Microsoft w ulepszaniu programu Visual Studio w czasie. Ten program [zbiera informacje o błędach,](../ide/diagnostic-data-collection.md)sprzęcie komputerowym i sposobie korzystania z programu Visual Studio bez przerywania użytkownikom zadań na komputerze. Zebrane informacje pomagają firmie Microsoft zidentyfikować funkcje, które należy ulepszyć. W tym dokumencie opisano sposób wyrażenia zgody na wykreślenie lub wykreślenie z programu VSCEIP.

[!INCLUDE [gdpr-hybrid-note](../misc/includes/gdpr-hybrid-note.md)]
> [!NOTE]
> Ustawienia danych telemetrycznych programu VSCEIP opt in in or out nie mają zastosowania do "Zgłoś problem" w programie Visual Studio. Gdy zgłaszasz dzienniki problemów są zbierane i wysyłane do firmy Microsoft tylko wtedy, gdy użytkownik udziela uprawnień, klikając przycisk "Prześlij". Jeśli jesteś zainteresowany zarządzaniem dziennikami przed przesłaniem do "Zgłoś problem", zobacz [Prywatność danych opinii,](./developer-community-privacy.md) aby uzyskać więcej informacji.

## <a name="opt-in-or-out"></a>Zgłośmy lub wyjmij

Program VSCEIP jest domyślnie włączony. Możesz go wyłączyć lub ponownie włączyć, postępując zgodnie z poniższymi instrukcjami:

1. W programie Visual Studio wybierz pozycję **Pomoc w** > **wysyłaniu opinii,** a następnie wybierz pozycję **Ustawienia**.

   Zostanie otwarte okno dialogowe **Program poprawy środowiska programu Visual Studio.**

1. Aby zrezygnować, wybierz **nie, nie chcę uczestniczyć**, a następnie wybierz **OK**. Aby się zdecydować, wybierz **opcję Tak, chcę wziąć udział,** a następnie wybierz **przycisk OK**.

   ![Okno dialogowe Programu poprawy środowiska programu Visual Studio](media/experience-improvement-program.png)

### <a name="registry-settings"></a>Ustawienia rejestru

W przypadku zainstalowania [narzędzia kompilacji dla programu Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2017)należy zaktualizować rejestr w celu skonfigurowania programu VSCEIP. Klienci korporacyjni mogą tworzyć zasady grupy, aby wyrazić zgodę na vsceip lub z nich zrezygnować, ustawiając zasady oparte na rejestrze.

Odpowiedni klucz rejestru i ustawienia są następujące:

::: moniker range="vs-2017"

- W 64-bitowym systemie operacyjnym klawisz = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\15.0\SQM**
- W 32-bitowym systemie operacyjnym klawisz = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\15.0\SQM**
- Gdy zasada grupy jest włączona, klucz = **HKEY_LOCAL_MACHINE\Oprogramowanie\Zasady\Microsoft\VisualStudio\SQM**

::: moniker-end

::: moniker range=">=vs-2019"

- W 64-bitowym systemie operacyjnym klawisz = **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VSCommon\16.0\SQM**
- W 32-bitowym systemie operacyjnym klawisz = **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSCommon\16.0\SQM**
- Gdy zasada grupy jest włączona, klucz = **HKEY_LOCAL_MACHINE\Oprogramowanie\Zasady\Microsoft\VisualStudio\SQM**

::: moniker-end

Wpis = **OptIn**

Wartość = (DWORD)

- **0** jest wyłączony (wyłącz VSCEIP)
- **1** jest wyz./a(włącz VSCEIP)

> [!CAUTION]
> Niepoprawne edytowanie rejestru może spowodować poważne uszkodzenie systemu. Przed wprowadzeniem zmian w rejestrze należy wykonać kopię zapasową wszystkich cennych danych, które znajdują się na komputerze. Można również użyć opcji uruchamiania **Ostatnia znana dobra konfiguracja,** jeśli wystąpią problemy po zastosowaniu ręcznych zmian.

Aby uzyskać więcej informacji na temat informacji gromadzonych, przetwarzanych lub przesyłanych przez program VSCEIP, zobacz [Zasady zachowania poufności informacji firmy Microsoft](https://privacy.microsoft.com/privacystatement).

## <a name="see-also"></a>Zobacz też

* [Informacje diagnostyczne zebrane przez program Visual Studio](diagnostic-data-collection.md)
* [Opcje opinii programu Visual Studio](../ide/feedback-options.md)
* [Jak zgłosić problem z programem Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md)
* [Społeczność deweloperów programu Visual Studio](https://developercommunity.visualstudio.com/)
* [Oświadczenie o ochronie prywatności w firmie Microsoft](https://privacy.microsoft.com/privacystatement)
