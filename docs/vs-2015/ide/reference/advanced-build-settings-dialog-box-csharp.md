---
title: Zaawansowane ustawienia kompilacji — okno dialogowe (C#) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- cs.AdvancedBuildSettings
helpviewer_keywords:
- Build options [C#], advanced
ms.assetid: 141f2dee-1563-4ce6-ba37-32920b082519
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 38f4d233c8804bec91d2f7dfd2dc34c6879e8be9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651723"
---
# <a name="advanced-build-settings-dialog-box-c"></a>Zaawansowane ustawienia kompilacji (C#) — Okno dialogowe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Za pomocą okna dialogowego **Ustawienia AdvancedBuild** **projektanta projektu** można określić zaawansowane właściwości konfiguracji kompilacji projektu. To okno dialogowe ma zastosowanie [!INCLUDE[csprcs](../../includes/csprcs-md.md)] tylko do projektów.

## <a name="general"></a>Ogólne
 Poniższe opcje umożliwiają ustawienie ogólnych ustawień zaawansowanych.

 **Wersja językowa** Określa wersję języka do użycia. Zestaw funkcji różni się w każdej wersji, dlatego można użyć tej opcji, aby wymusić, aby kompilator zezwalał tylko na podzbiór wdrożonych funkcji, lub aby włączyć tylko te funkcje, które są zgodne z istniejącym standardem. To ustawienie ma następujące opcje:

- **ISO-1**

   Dotyczy funkcji standardowych ISO-1.

- **wartooć**

   Odwołuje się do bieżącej wersji.

  Aby uzyskać więcej informacji, zobacz [/langversion (opcje kompilatora C#)](https://msdn.microsoft.com/library/3fb00b05-a0ff-4782-b313-13a4c0f62d94).

  **Raportowanie wewnętrznego błędu kompilatora** Określa, czy raportować błędy kompilatora do firmy Microsoft. Jeśli zostanie ustawiony **monit** (domyślnie), zostanie wyświetlony monit o podanie, czy wystąpił wewnętrzny błąd kompilatora, co umożliwia wysłanie raportu o błędach do firmy Microsoft. W przypadku wybrania opcji **Wyślij**raport o błędach zostanie wysłany automatycznie. W przypadku ustawienia wartości **Queue**raporty o błędach będą umieszczane w kolejce. W przypadku wybrania wartości **none**błąd będzie raportowany tylko w danych wyjściowych kompilatora. Aby uzyskać więcej informacji, zobacz [/errorreport (opcje kompilatora C#)](https://msdn.microsoft.com/library/bd0e7493-b79d-4369-9c3f-ba26ebdfbedf).

  **Sprawdź, czy jest przepełnienie arytmetyczne/nadmiarowy** Określa, czy instrukcja arytmetyczna liczb całkowitych, która nie znajduje się w zakresie [zaznaczonych](https://msdn.microsoft.com/library/718a1194-988d-48a3-b089-d6ee8bd1608d) lub [niesprawdzonych](https://msdn.microsoft.com/library/0c021f7c-923f-4b3d-a58f-55336f5ac27e) słów kluczowych i powoduje, że wartość spoza zakresu typu danych spowoduje wystąpienie wyjątku czasu wykonywania. Aby uzyskać więcej informacji, zobacz [/Checked (opcje kompilatora C#)](https://msdn.microsoft.com/library/fb7475d3-e6a6-4e6d-b86c-69e7a74c854b).

  **Nie Odwołuj się Do mscorlib.dll** Określa, czy mscorlib.dll zostanie zaimportowana do programu w celu zdefiniowania całej <xref:System> przestrzeni nazw. Zaznacz to pole wyboru, jeśli chcesz zdefiniować lub utworzyć własną <xref:System> przestrzeń nazw i obiekty. Aby uzyskać więcej informacji, zobacz [/nostdlib (opcje kompilatora C#)](https://msdn.microsoft.com/library/ec197989-fa49-4725-a455-e06b551eb65f).

## <a name="output"></a>Dane wyjściowe
 Poniższe opcje pozwalają określić zaawansowane opcje wyjściowe.

 **Informacje o debugowaniu** Określa typ informacji o debugowaniu generowanych przez kompilator. Informacje o sposobie konfigurowania wydajności debugowania aplikacji znajdują się w temacie [ułatwianie debugowania obrazu](https://msdn.microsoft.com/library/7d90ea7a-150f-4f97-98a7-f9c26541b9a3). To ustawienie ma następujące opcje:

- **brak**

   Określa, że nie będą generowane żadne informacje o debugowaniu

- **szczegółowe**

   Umożliwia dołączenie debugera do działającego programu.

- **pdbonly**

   Zezwala na Debugowanie kodu źródłowego, gdy program jest uruchamiany w debugerze, ale tylko w przypadku, gdy uruchomiony program zostanie dołączony do debugera.

  Aby uzyskać więcej informacji, zobacz [/debug (opcje kompilatora C#)](https://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).

  **Wyrównanie pliku** Określa rozmiar sekcji w pliku wyjściowym. Prawidłowe wartości to **512**, **1024**, **2048**, **4096**i **8192**. Te wartości są mierzone w bajtach. Każda sekcja zostanie wyrównana na granicy, która jest wielokrotnością tej wartości, co wpływa na rozmiar pliku wyjściowego. Aby uzyskać więcej informacji, zobacz [/filealign (opcje kompilatora C#)](https://msdn.microsoft.com/library/15cf1c98-3798-4ced-9f08-60619308a073).

  **Adres podstawowy biblioteki DLL** Określa preferowany adres podstawowy, z którego ma zostać załadowana Biblioteka DLL. Domyślny adres podstawowy dla biblioteki DLL jest ustawiany przez [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] środowisko uruchomieniowe języka wspólnego. Aby uzyskać więcej informacji, zobacz [/BaseAddress (opcje kompilatora C#)](https://msdn.microsoft.com/library/ce13c965-dfe4-4433-94f5-63b476e3a608).

## <a name="see-also"></a>Zobacz też
 Strona kompilacji [opcji kompilatora języka c#](https://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44) [, Projektant projektu (C#)](../../ide/reference/build-page-project-designer-csharp.md)
