---
title: Prywatne dane dla raportów problemów
ms.date: 06/21/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- developer community privacy
- privacy, developer community
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24ac5c42f91e7dbf4dac310d67fc710f75fc8309
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986855"
---
# <a name="developer-community-data-privacy"></a>Prywatność danych w społeczności deweloperów

Domyślnie, wszystkie informacje w problem raport dotyczący [społeczności deweloperów](https://developercommunity.visualstudio.com/), w tym wszelkie komentarze i odpowiedzi, jest widoczna publicznie. Jest to korzystne, ponieważ zezwala ona na całej społeczności wyświetlić problemy, rozwiązania i rozwiązania, które zostały znalezione w innych użytkowników. Jednak jeśli zajmującym się ochroną prywatności danych lub tożsamości dostępne opcje.

## <a name="identity-privacy"></a>Prywatność tożsamości

Jeśli jest sprawą przedstawiania swoją tożsamość, [Utwórz nowe konto Microsoft](https://signup.live.com/) nie ujawnia żadnych informacji o Tobie. Aby utworzyć raport, należy użyć tego konta.

## <a name="data-privacy"></a>Prywatność danych

Jeśli jesteś zajmującym się ochroną prywatności danych, nie należy umieszczać coś, co chcesz przechowywać prywatne w ramach tytułu lub zawartości elementu początkowego raportu zawsze jest publiczny. Zamiast tego należy utworzyć raport, a następnie zanotuj, będzie wysłanie szczegółów prywatnie w oddzielnych komentarz. Po utworzeniu raport o problemie możesz określić, kto może wyświetlać odpowiedzi i załączników:

1. W raporcie, możesz utworzyć, wybierz **Dodaj komentarz** do utworzenia prywatnej opis problemu.

2. W edytorze odpowiedzi formant poniżej **przesyłania** i **anulować** przycisków, aby określić odbiorców w odpowiedzi. Wybierz **Viewable moderatorzy i oryginalnego plakat** Aby ograniczyć widoczność, aby pracownicy firmy Microsoft i samodzielnie.

   ![Kontrolka ochrony prywatności w społeczność deweloperów](media/developer-community-privacy-control.png)

   Tylko osoby, które określisz zobaczyć komentarz i wszystkie obrazy, łącza lub kodu, które uwzględniasz w nim. Wszystkie odpowiedzi w ramach komentarza ma taką samą widoczność jak pierwotnego komentarza. Ta zasada obowiązuje, nawet wtedy, gdy kontroli prywatności w odpowiedzi na nie wyświetla stan widoczności ograniczeniami poprawnie.

3. Dodaj opis i wszelkie inne informacje, obrazy i załączniki plików potrzebnych do odtworzenia usługi. Wybierz **przesyłania** przycisk, aby wysyłać tych informacji przez użytkowników.

   > [!NOTE]
   > Istnieje limit 2 GB na dołączonych plików i maksymalnie 10 plików. Musisz przekazać większy plik, można przesłać nowy raport o problemie lub żądanie adresu URL przesyłania z pracownikiem firmy Microsoft w komentarzu prywatnych.

Aby zachować prywatność i zachować poufne informacje z widoku publicznego, powinien zachować ostrożność, aby zachować wszystkie interakcje z firmy Microsoft do odpowiedzi zgodnie z ograniczeniami widoczność komentarz. Odpowiadanie na komentarze innych może spowodować przypadkowe ujawnienie poufnych informacji.

## <a name="data-we-collect"></a>Zbierane dane

Jeśli **Zgłoś problem** jest inicjowane z Instalatora programu Visual Studio, zbierane są najnowsze dziennika instalacji.

Jeśli **Zgłoś problem** jest inicjowane z programu Visual Studio, zbierane są co najmniej jeden z następujących typów danych:

- Watson i .NET wpisów z dziennika zdarzeń

- Plik dziennika aktywności w pamięci w usłudze Visual Studio

- PerfWatson plików, gdy jest włączone zbieranie Watson, z *VSFeedbackPerfWatsonData* folderu

- Pliki dziennika LiveShare, jeśli istnieją, z *VSFeedbackVSRTCLogs* folderu

- Pliki dziennika platformy Xamarin, jeśli istnieją, z *%LOCALAPPDATA%\Xamarin\Logs*

- Pliki dziennika Nuget, jeśli istnieją, z *%TEMP%\NuGetScratch\nuget-dg\nugetSpec.dg*

- W sieci Web debugera pliki dziennika, jeśli nie istnieją:

   - *%TEMP%\vscode-chrome-debug.txt*

   - *%TEMP%\vscode-node-debug2.txt*

   - *%TEMP%\vscode-edge-debug.txt*

- Zrzut ekranu, jeśli chcesz dołączyć

- Rejestrowanie danych, jeśli chcesz uwzględnić nagranie, w tym:

   - Kroki umożliwiające odtworzenie problemu

   - Plik śledzenia ETL

   - Plik zrzutu

    > [!NOTE]
    > Możesz usunąć dowolne danych rejestrowania, które nie chcesz przesłać przed przesłaniem raportu.

## <a name="see-also"></a>Zobacz także

- [Jak zgłosić problem z programem Visual Studio](how-to-report-a-problem-with-visual-studio-2017.md)
- [Prywatność danych raportu problemu C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset#reports-and-privacy)