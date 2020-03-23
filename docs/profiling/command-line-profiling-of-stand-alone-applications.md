---
title: Profilowanie wiersza polecenia aplikacji autonomicznych | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profillng tools,stand-alone applications
- profling stand-alone applications
ms.assetid: a47f2bf2-186d-4120-bb79-34e2f3a1ee42
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3f80f3e65969973202af08299b07ebfa420f3bd2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77557856"
---
# <a name="command-line-profiling-of-stand-alone-applications"></a>Profilowanie wiersza polecenia aplikacji autonomicznych
W tej sekcji opisano procedury i opcje zbierania danych o wydajności [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dla aplikacji autonomicznych (klienckich) przy użyciu narzędzi profilowania z wiersza polecenia.

## <a name="common-tasks"></a>Typowe zadania

| Zadanie | Zawartość pokrewna |
| - | - |
| **Zbieranie statystyk aplikacji:** Użyj metody próbkowania do zbierania statystyk wydajności. Próbkowanie danych jest przydatne do analizowania problemów z wykorzystaniem procesora CPU i do zrozumienia ogólnych cech wydajności aplikacji. | -   [Zbieranie statystyk aplikacji przy użyciu próbkowania](../profiling/collecting-application-statistics-for-stand-alone-applications.md) |
| **Zbieranie szczegółowych danych dotyczących chronometrażu:** Metoda instrumentacji służy do zbierania szczegółowych informacji o czasie. Dane instrumentacji są przydatne do analizowania problemów we/wy i do szczegółowej analizy scenariuszy aplikacji. | -   [Zbieranie szczegółowych danych dotyczących chronometrażu za pomocą oprzyrządowania](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md) |
| **Zbieranie danych pamięci platformy .NET:** Próbkowanie lub instrumentacji służy do zbierania danych alokacji pamięci .NET, które pokazują rozmiar i liczbę przydzielonych obiektów. Można również zbierać dane okresu istnienia obiektu, który pokazuje rozmiar i liczbę obiektów, które są odzyskane w każdej generacji wyrzucania elementów bezużytecznych. | -   [Zbieranie danych pamięci programu .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md) |
| **Zbieranie danych współbieżności:** Użyj metody współbieżności do zbierania danych rywalizacji o zasoby i danych aktywności wątku, które pokazują wykorzystanie procesora CPU, rywalizację wątków, migrację wątków, opóźnienia synchronizacji, obszary nakładających się we/wy i inne zdarzenia systemowe. | -   [Zbieranie danych współbieżności](../profiling/collecting-concurrency-data-for-stand-alone-applications.md) |
| **Dodawanie danych interakcji warstwy:** Można dodać dane dotyczące wydajności synchronii ADO.NET wywołania, które [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] aplikacja została wykonana do bazy danych firmy Microsoft. Dodawanie danych interakcji warstwy do przebiegu profilowania wymaga określonych procedur za pomocą narzędzi do profilowania wiersza polecenia. | -   [Zbieranie danych interakcji warstwy](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>Zadania powiązane

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Aplikacje ASP.NET profilowe**|-   [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
|**Usługi profilowania**|-   [Usługi profilowania](../profiling/command-line-profiling-of-services.md)|
