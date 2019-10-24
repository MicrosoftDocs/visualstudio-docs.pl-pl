---
title: Przykłady tworzenia aplikacji mobilnych dla wielu platform | Microsoft Docs
ms.custom: ''
ms.date: 10/17/2019
ms.technology: vs-ide-mobile
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: bc384c12-fccc-45d7-9fb9-b90d536aa663
author: corob-msft
ms.author: corob
manager: jillfra
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: 8eb8b53da30f0c0896ac9576407d34f9a2f9bdbc
ms.sourcegitcommit: 57bc1c3887838d707c13feff72a677b3bad3be4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72777710"
---
# <a name="cross-platform-mobile-development-examples"></a>Przykłady programowania międzyplatformowych aplikacji mobilnych

Kilka szablonów zainstalowanych przez **Programowanie aplikacji mobilnych za pomocą C++**  obciążeń generuje kompletne przykłady, których można użyć do uzyskania informacji. Ponadto Centrum deweloperów systemu Windows zawiera kilka przykładowych aplikacji, które można pobrać i wypróbować w programie Visual Studio.

- [Przykład aplikacji Hello-JNI dla systemu Android](https://code.msdn.microsoft.com/hello-jni-Android-790ab73d)

   Ten przykład to port aplikacji Hello-JNI systemu Android NDK. Przykład ilustruje kompleksową aplikację natywnego interfejsu Java "Hello world". Ładuje ciąg z metody natywnej zaimplementowanej w bibliotece udostępnionej, a następnie wyświetla ją w aplikacji.

- [Przykład aplikacji Hello-GL2 dla systemu Android](https://code.msdn.microsoft.com/hello-gl2-Android-3b61896c)

   Ten przykład to port aplikacji Hello-GL2 systemu Android NDK. W przykładzie przedstawiono kompleksową aplikację języka Java natywnego interfejsu systemu Android OpenGL. Renderuje Trójkąt przy użyciu interfejsów API modułu cieniującego OpenGL ES 2,0.

- [Przykładowa aplikacja Android plazmy plazmowej](https://code.msdn.microsoft.com/Bitmap-Plasma-Android-77ae296a)

   Ten przykład to port aplikacji plazmowej mapy bitowej systemu Android NDK. W przykładzie przedstawiono kompleksową aplikację Java natywnego interfejsu Android OpenGL ES 2,0. Pokazuje bezpośrednie manipulowanie buforami pikseli mapy bitowej systemu Android w celu wygenerowania efektu osocza.

- [Przykład biblioteki TwoLibs dla systemu Android](https://code.msdn.microsoft.com/TwoLibs-Android-Library-6396e5c4)

   Ten przykład to port przykładu TwoLibs NDK dla systemu Android. Używa ona zarówno dynamicznie załadowanej biblioteki udostępnionej, jak C++ i statycznej biblioteki natywnej systemu Android, która implementuje metodę wywoływaną z natywnej aplikacji interfejsu Java. Ten przykład jest dobrym punktem wyjścia dla deweloperów, aby zrozumieć, jak używać statycznych/dynamicznych bibliotek udostępnionych do tworzenia kompleksowej aplikacji JNI dla systemu Android za pomocą programu Visual Studio.

- [Przykład aplikacji dla systemu Android z herbaty pot](https://code.msdn.microsoft.com/Tea-Pot-Android-Application-e7c05d73)

   Ten przykład jest portem aplikacji czajniczek dla systemu Android NDK. W przykładzie przedstawiono kompleksową aplikację Java natywnego interfejsu Android OpenGL ES 2,0.

- [Przykład aplikacji MoreTeaPots dla systemu Android](https://code.msdn.microsoft.com/MoreTeaPots-Android-a9bd8549)

   Ten przykład jest portem aplikacji MoreTeaPots dla systemu Android NDK. W przykładzie przedstawiono kompleksową aplikację języka Java natywnego interfejsu systemu Android OpenGL.

- [Przykład biblioteki test-libstdcpp dla systemu Android](https://code.msdn.microsoft.com/test-libstdcpp-Android-00b548f5)

   Ten przykład jest portem zestawu Android NDK test-libstdc + +, przeznaczonym do użycia z programem Visual Studio. Ten przykład jest dobrym punktem wyjścia dla deweloperów, aby zrozumieć, jak korzystać z biblioteki standardowej.

  Aby otworzyć jeden z przykładów w programie Visual Studio, Pobierz plik zip i Otwórz stronę **Właściwości** pobranego pliku w Eksploratorze. Wybierz przycisk **Odblokuj** , a następnie wybierz **OK**. Wyodrębnij zawartość pliku zip do wygodnej lokalizacji, a następnie otwórz C++ folder w wyodrębnionym przykładzie i Otwórz plik rozwiązania.

  Aby skompilować przykład, naciśnij klawisz **F7**lub na pasku menu wybierz **kompilacja**, **Skompiluj rozwiązanie**.
