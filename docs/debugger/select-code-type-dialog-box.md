---
title: Okno dialogowe Wybieranie typu kodu | Microsoft Docs
ms.date: 06/12/2020
ms.topic: reference
f1_keywords:
- vs.debug.selectengines
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- debugging [Visual Studio], engine selection
- debugger, engine selection
- debugging engine selection dialog box
no-loc:
- Blazor WebAssembly
ms.assetid: 932269fe-94e3-43cb-8931-078f31afd177
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a6fefcea57b97ad3b31e4d10330756565c005184
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "88248777"
---
# <a name="select-code-type-dialog-box"></a>Wybór typu kodu — Okno dialogowe

Aby otworzyć to okno dialogowe, Otwórz okno dialogowe **Dołącz do procesu** , a następnie kliknij przycisk **Wybierz** .

**Automatycznie Określ typ kodu do debugowania** Odpowiedni debuger zostanie wybrany na podstawie rodzaju kodu, który jest uruchomiony.

**Debuguj te typy kodu:** Z podanej listy wybierz typy kodu, które chcesz debugować. Może to być przydatne w przypadku [rozwiązywania problemów z awarią](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md#BKMK_Troubleshoot_attach_errors). Ta opcja ogranicza wykrywanie tylko do tych typów kodu, które mają być debugowane.

::: moniker range=">=vs-2019"
- Blazor WebAssembly -Po stronie klienta Blazor WebAssembly
- Procesor GPU — kod w języku C++ uruchomiony na emulatorze oprogramowania procesora GPU
- JavaScript (Chrome) — kod JavaScript działający w programie Chrome
- JavaScript (Microsoft Edge-chrom) — JavaScript działający w programie Microsoft Edge opartym na chromie dla systemu Windows 10
- Debuger CDP języka JavaScript (V3) — program Chrome DevTools Protocol w wersji 3 używany do debugowania w kliencie CDP
- Zarządzane (CoreCLR) — .NET Core
- Zarządzane (kompilacja natywna) — kod języka C++/CLR
- Zarządzany (v 3.5, v 3.0, v 2.0) — kod .NET Framework dla .NET Framework 2,0 i wyższych (do 3,5)
- Zarządzany (v. 4.6, v 4.5, v 4.0) — kod .NET Framework dla .NET Framework 4,0 i wyższych
- Native-C/C++
- Node.js debugowanie — kod hostowany przez środowisko uruchomieniowe Node.js
- Python — Python 
- Skrypt — określa ogólny debuger skryptów dla języka JavaScript. Użyj bardziej restrykcyjnych opcji, jeśli mają zastosowanie do danego scenariusza, takiego jak JavaScript (Chrome).
- T-SQL — Transact-SQL
- Unity — Unity
- Zarządzany tryb zgodności — określa starszy debuger dla kodu zarządzanego, używany zwykle w debugowaniu w trybie mieszanym z kodem języka C++/CLR (umożliwia edytowanie i kontynuowanie w trybie mieszanym) lub do obsługi rozszerzeń przeznaczonych dla starszego debugera. W większości scenariuszy debugowania w trybie mieszanym wybierz opcję **natywny** i odpowiedni typ kodu **zarządzanego** zamiast zarządzanego trybu zgodności.
::: moniker-end

W przypadku większości scenariuszy dołączania wielu debugerów w tej samej sesji debugowania nie jest obsługiwane. Możesz to zrobić przy użyciu drugiego wystąpienia programu Visual Studio.

## <a name="see-also"></a>Zobacz też
- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Dołączanie do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
