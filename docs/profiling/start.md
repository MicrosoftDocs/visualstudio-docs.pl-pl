---
title: Start | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df1e76c895102d5a33d66628a7c6436ab604b1ba
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56639768"
---
# <a name="start"></a>Uruchamianie
**Start** jest opcja *VSPerfCmd.exe* opcja, która inicjuje profiler do określonej metody profilowania.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName [Options]
```

#### <a name="parameters"></a>Parametry
 `Method` Musi mieć jedną z następujących słów kluczowych:

-   **ŚLEDZENIE** -określa metody instrumentacji.

-   **Przykładowe** -określa metody pobierania próbek.

-   **POKRYCIE** -określa pokrycie kodu.

-   **WSPÓŁBIEŻNOŚĆ** -określa metodę rywalizacji zasobów.

## <a name="required-options"></a>Wymagane opcje
 **Dane wyjściowe** opcja musi być określony, gdy **Start** jest określona w wierszu polecenia.

 **Dane wyjściowe:** `filename` Określa nazwę pliku wyjściowego.

## <a name="exclusive-options"></a>Wykluczających się opcji
 Następujące opcje można używać tylko z **Start** opcji w wierszu polecenia.

 **CrossSession**&#124;**CS** międzyprocesowe Włącza profilowanie. Nazwy opcji **CrossSession** i **CS** są obsługiwane.

 **Użytkownik:**[`domain\`]`username` umożliwia dostęp klienta do monitora z określonego konta.

 **WinCounter:** `Path` [**Automark**:`n`] **WinCounter** Określa licznik wydajności Windows, aby uwzględnić jako znacznik w pliku danych profilowania. **AutoMark** Określa interwał w milisekundach między operacjami pliku danych.

## <a name="invalid-options"></a>Nieprawidłowe opcje
 Nie można użyć następujących opcji z **Start** opcji w wierszu polecenia.

 **Stan** **stan** dotyczy procesy, które są profilowane. Wyświetla listę procesów i wątków oraz ich bieżącego stanu profilowania (wł. / wył.). Na przykład, jeśli proces zostanie zatrzymana **stan** nie wskaże, to w raporcie. **Stan** opisano proces albo jest profilowane czy nie.

 **Zamknięcie**[**:**`Timeout`] wyłącza profilera.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje sposób użycia *VSPerfCmd.exe* **Start** możliwość zainicjowania programu profilującego.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)