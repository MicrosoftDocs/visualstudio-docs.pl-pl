---
title: Właściwości sesji wydajności | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,properties
- property pages,Profiling Tools
- performance tools, performance session properties
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1b3bafa976c8e57f468a3f3f59a3b6b19308fd1b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74772205"
---
# <a name="performance-session-properties"></a>Właściwości sesji wydajności

Sesja **wydajności** umożliwia skonfigurowanie ustawień, które określają sposób profilowania aplikacji. Przechowuje również raporty, które są generowane dla sesji profilowania.

**Sesja wydajności** jest tworzęna przez uruchomienie **Kreatora wydajności** lub ręczne utworzenie sesji. Sesja **wydajności** jest wyświetlana w **Eksploratorze wydajności** po utworzeniu sesji **wydajności.**

Aby wyświetlić właściwości **sesji wydajności,** zaznacz nazwę sesji w **Eksploratorze wydajności,** kliknij ją prawym przyciskiem myszy, a następnie wybierz polecenie **Właściwości**.

Sesja wydajności ma następujące strony właściwości:

## <a name="general"></a>Ogólne

Te ustawienia umożliwiają wybranie metody profilowania, dodanie danych zbierania obiektów i okresu istnienia obiektu .NET oraz określenie domyślnej lokalizacji raportu i konwencji nazewnictwa.

Aby uzyskać więcej informacji, zobacz:

[Jak: Wybierz metody zbierania](../profiling/how-to-choose-collection-methods.md)

[Zbieranie danych alokacji pamięci .NET i okresu istnienia](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

- [Instrukcje: ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)

## <a name="launch"></a>Uruchom

Te ustawienia umożliwiają wybranie z listy plików binarnych i określenie kolejności rozpoczęcia plików binarnych.

Aby uzyskać więcej informacji, zobacz [Jak: Określanie pliku binarnego, aby rozpocząć](../profiling/how-to-specify-the-binary-to-start.md)

## <a name="sampling"></a>Próbkowanie

Te ustawienia umożliwiają wybranie zdarzenia próbki i interwału próbkowania, gdy próbkowanie jest używane jako metoda profilowania. Przykładowe zdarzenie służy do zbierania danych profilowania w określonym przedziale czasu. Na przykład jeśli zdarzenie próbki jest cykle zegara i interwał próbkowania jest ustawiona na 10,000,000 następnie profilowania danych są zbierane po każdym 10 milionów cykli zegara. Dostępne są następujące cztery typy przykładowych zdarzeń:

- Clock Cycles - dla problemów związanych z procesorem
- Błędy strony - w przypadku problemów związanych z pamięcią
- Wezwania systemowe - w przypadku problemów związanych z we/wy
- Liczniki wydajności - w przypadku problemów z wydajnością niskiego poziomu
- Dodatkowe przykładowe zdarzenia można określić na podstawie dostępnych liczników wydajności

Aby uzyskać więcej informacji, zobacz [Jak: Wybieranie zdarzeń próbkowania](../profiling/how-to-choose-sampling-events.md)

## <a name="binary"></a>plików binarnych
Te ustawienia umożliwiają określenie, czy chcesz przenieść instrumentowany plik binarny do innej lokalizacji. Na przykład, jeśli profilowanie *My.DLL* i nie wybrać, aby przenieść instrumentowane binarne, kopia zapasowa *My.DLL* o nazwie *My.Orig.DLL* jest tworzony. Następnie *my.DLL* jest modyfikowany przez wstawianie sond do zbierania danych. Jeśli zdecydujesz się przenieść instrumentowany plik binarny, oryginalny plik binarny nie zostanie zmieniona, a instrumentowany plik binarny zostanie skopiowany do określonej lokalizacji do użycia podczas instrumentacji.

Aby uzyskać więcej informacji, zobacz [Jak: Określanie pliku binarnego, aby rozpocząć](../profiling/how-to-specify-the-binary-to-start.md)

## <a name="tier-interactions"></a>Interakcje warstw

Aby uzyskać więcej informacji, zobacz [Zbieranie danych interakcji warstwy](../profiling/collecting-tier-interaction-data.md)

## <a name="instrumentation"></a>Oprzyrządowanie

Te ustawienia umożliwiają zbieranie danych o wydajności [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] kodu JScript na stronach sieci Web i określanie zdarzeń **przed instrumentem** i **po instrumencie,** które mają wystąpić przed lub po procesie instrumentacji.

Aby uzyskać więcej informacji, zobacz:

[Jak: Profil kodu JavaScript na stronach internetowych](../profiling/how-to-profile-javascript-code-in-web-pages.md)

[Instrukcje: określanie poleceń przed i po instrumentacji](../profiling/how-to-specify-pre-and-post-instrument-commands.md)

## <a name="cpu-counters"></a>Liczniki procesorów

Te ustawienia umożliwiają zbieranie danych o licznikach wydajności procesora CPU podczas korzystania z metody profilowania instrumentacji. Przenośne liczniki wydajności są dostępne niezależnie od konstrukcji procesora lub producenta. Zdarzenia platformy są specyficzne dla projektu procesora i producenta. Aby uzyskać więcej informacji na temat liczników wydajności na chipie, zobacz dokumentację określonego procesora.

Aby uzyskać więcej informacji, zobacz [Jak: Zbieranie danych licznika procesora](../profiling/how-to-collect-cpu-counter-data.md)

## <a name="windows-events"></a>Zdarzenia systemu Windows

Podczas profilowania można zbierać dane od dostawców śledzenia zdarzeń. Dane można wyświetlić za pomocą opcji narzędzia `/calltrace` wiersza polecenia *VSPerfReport.exe.* Aby uzyskać więcej informacji na temat śledzenia zdarzeń dla systemu Windows (ETW), zobacz [Informacje o śledzeniu zdarzeń](/windows/win32/etw/about-event-tracing).

Aby uzyskać więcej informacji, zobacz:

[Instrukcje: zbieranie danych śledzenia zdarzeń dla systemu Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)

[VSPerfReport](../profiling/vsperfreport.md).

## <a name="windows-counters"></a>Liczniki systemu Windows

Ta opcja umożliwia zbieranie danych z liczników Monitora wydajności systemu Windows. Aby zebrać te dane, zaznacz pole wyboru z etykietą **Zbieraj liczniki wydajności systemu Windows**. Interwał kolekcji można ustawić w polu **Interwał zbierania.** **Kategoria licznika** i **wystąpienie** mogą być również dostępne. Dostępne są niektóre domyślne liczniki Monitora wydajności systemu Windows.

 Aby uzyskać więcej informacji, zobacz [Jak: Zbieranie danych licznika systemu Windows](../profiling/how-to-collect-windows-counter-data.md).

## <a name="advanced"></a>Zaawansowane

Te ustawienia umożliwiają dodawanie opcji do procesu instrumentacji przez określenie jednej lub więcej opcji narzędzia do profilowania wiersza polecenia [VSInstr.](../profiling/vsinstr.md) Można również określić wersję wspólnego środowiska uruchomieniowego do profilu, gdy aplikacja używa więcej niż jednej wersji.

Aby uzyskać więcej informacji, zobacz:

[Instrukcje: określanie środowiska uruchomieniowego programu .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)

[Instrukcje: określanie dodatkowych opcji instrumentacji](../profiling/how-to-specify-additional-instrumentation-options.md)

## <a name="see-also"></a>Zobacz też

[Przeglądy](../profiling/overviews-performance-tools.md)
[Konfigurowanie sesji](../profiling/configuring-performance-sessions.md)
wydajności[Kontrolowanie zbierania danych](../profiling/controlling-data-collection.md)
