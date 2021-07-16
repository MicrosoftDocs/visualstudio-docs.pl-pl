---
title: Wariant formatu docelowego renderowania 16bpp | Microsoft Docs
description: Zastosuj wariant formatu docelowego renderowania 16 bitów na piksel (bpp), ustawiając format pikseli na wartość DXGI_FORMAT_B5G6R5_UNORM dla wszystkich obiektów docelowych renderowania i buforów wstecz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 96f202663b1b325f7a4ac86876abc94563a02fb2
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232872"
---
# <a name="16-bpp-render-target-format-variant"></a>Wariant formatu docelowego renderowania 16 bpp
Ustawia format pikseli na DXGI_FORMAT_B5G6R5_UNORM dla wszystkich obiektów docelowych renderowania i buforów wstecz.

## <a name="interpretation"></a>Interpretacja
 Docelowy lub back bufor renderowania zwykle używa formatu 32 bpp (32 bity na piksel), takiego jak B8G8R8A8_UNORM. Formaty 32-bpp mogą zużywać dużą przepustowość pamięci. Ponieważ format B5G6R5_UNORM to format 16 bpp, który jest o połowę mniejszy niż formaty 32-bpp, użycie go może zmniejszyć obciążenie przepustowości pamięci, ale kosztem większej wierności kolorów.

 Jeśli ten wariant pokazuje duży wzrost wydajności, prawdopodobnie oznacza to, że aplikacja zużywa zbyt dużo przepustowości pamięci. Możesz uzyskać znaczącą poprawę wydajności, szczególnie gdy profilowana ramka miała znaczącą ilość narysowania lub mieszania alfa.

Format docelowy renderowania 16-bpp może zmniejszyć pasm pamięci z użyciem, gdy aplikacja ma następujące warunki:
- Nie wymaga reprodukowania kolorów o wysokiej jakości.
- Nie wymaga kanału alfa.
- Nie ma często płynnych gradientów (które są podatne na artefakty pasmowania z niższą wiernością kolorów).

Inne strategie zmniejszenia przepustowości pamięci obejmują:
- Zmniejsz ilość narysowania lub mieszania alfa.
- Zmniejsz wymiary buforu ramki.
- Zmniejsz wymiary zasobów tekstury.
- Zmniejszenie kompresji zasobów tekstury.

Jak zwykle należy wziąć pod uwagę jakość obrazu, które są zapewniane przez dowolną z tych optymalizacji.

Aplikacje, które są częścią łańcucha wymiany, mają format buforu powrotu (DXGI_FORMAT_B5G6R5_UNORM), który nie obsługuje 16 bpp. Te łańcuchy wymiany są tworzone przy użyciu lub `D3D11CreateDeviceAndSwapChain` `IDXGIFactory::CreateSwapChain` . Aby omiń to ograniczenie, wykonaj następujące czynności:
1. Utwórz docelowy B5G6R5_UNORM format renderowania przy użyciu funkcji `CreateTexture2D` i renderuj do tego obiektu docelowego.
2. Skopiuj element docelowy renderowania na element backbuffer łańcucha wymiany, rysując czworokąt w trybie pełnoekranowym z celem renderowania jako teksturą źródłową.
3. Wywołaj wywołanie Obecne w łańcuchu wymiany.

   Jeśli ta strategia zaoszczędzy większą przepustowość niż jest zużywana przez skopiowanie obiektu docelowego renderowania do buforu wstecz łańcucha wymiany, wydajność renderowania zostanie zwiększona.

   Architektury procesora GPU korzystające z technik renderowania kafelków mogą uzyskać znaczące korzyści w wydajności dzięki użyciu formatu buforu ramowego 16 bpp. To ulepszenie wynika z tego, że większa część buforu ramek może zmieścić się w lokalnej pamięci podręcznej bufora ramek każdego kafelka. Architektury renderowania kafelkowego są czasami dostępne w procesorach GPU w komputerach przenośnych i tabletach. Rzadko pojawiają się poza tą niszą.

## <a name="remarks"></a>Uwagi
 Format docelowy renderowania jest resetowany do DXGI_FORMAT_B5G6R5_UNORM każdym wywołaniu obiektu , które `ID3D11Device::CreateTexture2D` tworzy obiekt docelowy renderowania. W szczególności format jest zastępowany, gdy obiekt D3D11_TEXTURE2D_DESC przekazany w pDesc opisuje obiekt docelowy renderowania; Czyli:

- Członek BindFlags ma D3D11_BIND_REDNER_TARGET flagę.

- Członek BindFlags ma wyczysz D3D11_BIND_DEPTH_STENCIL flagę.

- Dla członka Usage (Użycie) ustawiono wartość D3D11_USAGE_DEFAULT.

## <a name="restrictions-and-limitations"></a>Ograniczenia
 Ponieważ format B5G6R5 nie ma kanału alfa, zawartość alfa nie jest zachowywana przez ten wariant. Jeśli renderowanie aplikacji wymaga kanału alfa w docelowym celu renderowania, nie można po prostu przełączyć się do formatu B5G6R5.

## <a name="example"></a>Przykład
 Wariant **formatu docelowego renderowania 16 bpp** można odtworzyć dla obiektów docelowych renderowania utworzonych przy użyciu `CreateTexture2D` kodu w ten sposób:

```cpp
D3D11_TEXTURE2D_DESC target_description;

target_description.BindFlags = D3D11_BIND_RENDER_TARGET;
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);
```
