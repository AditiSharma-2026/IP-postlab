import os
import cv2
import numpy as np
import base64
from flask import Flask, render_template_string, request, jsonify

app = Flask(__name__)
UPLOAD_FOLDER = 'uploads'
os.makedirs(UPLOAD_FOLDER, exist_ok=True)


# Helper function: Convert OpenCV image matrix to Base64 for web rendering
def img_to_base64(img):
    if img is None:
        return ""
    _, buffer = cv2.imencode('.png', img)
    return base64.b64encode(buffer).decode('utf-8')


# HTML + CSS (Tailwind) + JS Frontend Template
HTML_TEMPLATE = """
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Image Processing Lab</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
</head>
<body class="bg-slate-900 text-white min-h-screen flex flex-col font-sans">

    <!-- Header -->
    <header class="bg-slate-800 border-b border-slate-700 p-4 text-center shadow-lg">
        <h1 class="text-3xl font-extrabold text-transparent bg-clip-text bg-gradient-to-r from-blue-400 to-emerald-400">
            <i class="fa-solid fa-eye mr-2"></i> Image Processing Lab
        </h1>
    </header>

    <div class="flex flex-1 flex-col md:flex-row">
        <!-- Sidebar Controls -->
        <aside class="w-full md:w-1/3 bg-slate-800/50 p-6 border-r border-slate-700 flex flex-col gap-6">
            <div>
                <label class="block text-sm font-semibold mb-2 text-slate-300">Select Aim / Experiment</label>
                <select id="aimSelect" onchange="toggleInputs()" class="w-full p-3 rounded-lg bg-slate-900 border border-slate-600 focus:outline-none focus:border-blue-500 text-white text-sm">
                    <option value="aim1">Aim 1: Format Conversions, Arithmetic & Bitwise Operations</option>
                    <option value="aim2">Aim 2: 2-D Geometric Transformations (Translation, Rotation, Scaling, Shearing, Reflection, Cropping)</option>
                    <option value="aim3">Aim 3: Spatial Enhancement (Histogram Equalization, Sharpening, Thresholding)</option>
                    <option value="aim4">Aim 4: Spatial Domain Filtering (Averaging, Gaussian, Median, Bilateral)</option>
                    <option value="aim5">Aim 5: Image Inpainting (Telea & Navier-Stokes Methods)</option>
                    <option value="aim6">Aim 6: Lossless Compression & File Size Analysis</option>
                    <option value="aim7">Aim 7: Morphological Operations (Erosion, Dilation, Opening, Closing)</option>
                    <option value="aim8">Aim 8: Object Detection using Correlation Principle</option>
                    <option value="aim9">Aim 9: Background Illumination Correction (Top-Hat Transform)</option>
                    <option value="aim10">Aim 10: Colour Space Conversions (RGB, HSV, YCrCb, Lab)</option>
                    <option value="aim11">Aim 11: Edge Detection (Canny vs Sobel vs Prewitt)</option>
                </select>
            </div>

            <!-- Upload Inputs -->
            <form id="uploadForm" class="flex flex-col gap-4">
                <div>
                    <label class="block text-sm font-semibold mb-1 text-slate-300">Primary Image Input</label>
                    <input type="file" id="mainImage" accept="image/*" required class="w-full text-sm text-slate-400 file:mr-4 file:py-2 file:px-4 file:rounded-full file:border-0 file:text-sm file:font-semibold file:bg-blue-600 file:text-white hover:file:bg-blue-700 cursor-pointer"/>
                </div>

                <!-- Secondary Image Input (Only for Aim 8 Correlation) -->
                <div id="secondImgGroup" class="hidden">
                    <label class="block text-sm font-semibold mb-1 text-amber-400">Template Image (Small Object to Search)</label>
                    <input type="file" id="templateImage" accept="image/*" class="w-full text-sm text-slate-400 file:mr-4 file:py-2 file:px-4 file:rounded-full file:border-0 file:text-sm file:font-semibold file:bg-amber-600 file:text-white hover:file:bg-amber-700 cursor-pointer"/>
                </div>

                <button type="submit" class="w-full py-3 bg-gradient-to-r from-blue-500 to-emerald-500 hover:from-blue-600 hover:to-emerald-600 text-white font-bold rounded-lg shadow-lg transition duration-200">
                    Run Experiment
                </button>
            </form>

            <div id="infoBox" class="text-sm bg-slate-900/80 p-3 rounded-lg text-emerald-400 border border-emerald-500/30 hidden"></div>
        </aside>

        <!-- Main Output Panel -->
        <main class="flex-1 p-6 overflow-y-auto">
            <h2 class="text-xl font-bold mb-4 text-slate-200">Output Visualizations</h2>

            <div id="outputGrid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
                <div class="text-slate-500 italic col-span-full text-center py-12">
                    Select an Aim, upload the required image(s), and click "Run Experiment" to observe outputs.
                </div>
            </div>
        </main>
    </div>

    <script>
        function toggleInputs() {
            const aim = document.getElementById('aimSelect').value;
            const secondGroup = document.getElementById('secondImgGroup');
            if (aim === 'aim8') {
                secondGroup.classList.remove('hidden');
            } else {
                secondGroup.classList.add('hidden');
            }
        }

        document.getElementById('uploadForm').addEventListener('submit', async (e) => {
            e.preventDefault();
            const aim = document.getElementById('aimSelect').value;
            const mainImg = document.getElementById('mainImage').files[0];
            const tempImg = document.getElementById('templateImage').files[0];

            if (!mainImg) return alert("Please select a main image!");

            const formData = new FormData();
            formData.append('aim', aim);
            formData.append('image', mainImg);
            if (tempImg) formData.append('image2', tempImg);

            const grid = document.getElementById('outputGrid');
            grid.innerHTML = `<div class="col-span-full text-center py-12"><i class="fa-solid fa-spinner fa-spin text-4xl text-blue-500"></i><p class="mt-2 text-slate-400">Processing image pipeline...</p></div>`;

            try {
                const res = await fetch('/process', { method: 'POST', body: formData });
                const data = await res.json();

                grid.innerHTML = '';
                const infoBox = document.getElementById('infoBox');

                if (data.info) {
                    infoBox.innerText = data.info;
                    infoBox.classList.remove('hidden');
                } else {
                    infoBox.classList.add('hidden');
                }

                for (const [title, base64Str] of Object.entries(data.images)) {
                    const card = document.createElement('div');
                    card.className = "bg-slate-800 rounded-xl overflow-hidden border border-slate-700 shadow-md flex flex-col";
                    card.innerHTML = `
                        <div class="p-3 bg-slate-700/50 border-b border-slate-600 font-semibold text-sm text-slate-200">${title}</div>
                        <div class="p-2 flex-1 flex items-center justify-center bg-black/20">
                            <img src="data:image/png;base64,${base64Str}" class="max-h-64 object-contain rounded"/>
                        </div>
                    `;
                    grid.appendChild(card);
                }
            } catch (err) {
                grid.innerHTML = `<div class="col-span-full text-red-400 text-center py-12">An error occurred while executing the algorithm.</div>`;
            }
        });
    </script>
</body>
</html>
"""


@app.route('/')
def index():
    return render_template_string(HTML_TEMPLATE)


@app.route('/process', methods=['POST'])
def process():
    aim = request.form.get('aim')
    file = request.files.get('image')
    file2 = request.files.get('image2')

    if not file:
        return jsonify({'error': 'No image uploaded'}), 400

    img_path = os.path.join(UPLOAD_FOLDER, file.filename)
    file.save(img_path)
    img = cv2.imread(img_path)

    output_imgs = {}
    info_text = ""

    # --- AIM 1: Format Conversions, Arithmetic & Bitwise Operations ---
    if aim == 'aim1':
        gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
        inverted = cv2.bitwise_not(img)
        bright = cv2.add(img, np.ones(img.shape, dtype="uint8") * 50)
        output_imgs['Original Image'] = img_to_base64(img)
        output_imgs['Grayscale Format'] = img_to_base64(gray)
        output_imgs['Bitwise NOT (Inverted)'] = img_to_base64(inverted)
        output_imgs['Arithmetic Addition (+50 Brightness)'] = img_to_base64(bright)

    # --- AIM 2: 2-D Geometric Transformations ---
    elif aim == 'aim2':
        h, w = img.shape[:2]
        # Translation
        M_trans = np.float32([[1, 0, 50], [0, 1, 50]])
        translated = cv2.warpAffine(img, M_trans, (w, h))
        # Rotation
        M_rot = cv2.getRotationMatrix2D((w // 2, h // 2), 45, 1)
        rotated = cv2.warpAffine(img, M_rot, (w, h))
        # Scaling
        scaled = cv2.resize(img, (None, None), fx=0.5, fy=0.5)
        # Shearing
        M_shear = np.float32([[1, 0.2, 0], [0.2, 1, 0]])
        sheared = cv2.warpAffine(img, M_shear, (int(w * 1.2), int(h * 1.2)))
        # Reflection
        reflected = cv2.flip(img, 1)
        # Cropping
        cropped = img[int(h * 0.2):int(h * 0.8), int(w * 0.2):int(w * 0.8)]

        output_imgs['i) Translation'] = img_to_base64(translated)
        output_imgs['ii) Rotation (45°)'] = img_to_base64(rotated)
        output_imgs['iii) Scaling (0.5x)'] = img_to_base64(scaled)
        output_imgs['iv) Shearing'] = img_to_base64(sheared)
        output_imgs['v) Reflection (Horizontal)'] = img_to_base64(reflected)
        output_imgs['vi) Cropping'] = img_to_base64(cropped)

    # --- AIM 3: Spatial Domain Enhancement ---
    elif aim == 'aim3':
        gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
        hist_eq = cv2.equalizeHist(gray)
        kernel = np.array([[0, -1, 0], [-1, 5, -1], [0, -1, 0]])
        sharpened = cv2.filter2D(img, -1, kernel)
        _, thresh = cv2.threshold(gray, 127, 255, cv2.THRESH_BINARY)

        output_imgs['Histogram Equalization'] = img_to_base64(hist_eq)
        output_imgs['Spatial Sharpening'] = img_to_base64(sharpened)
        output_imgs['Intensity Thresholding'] = img_to_base64(thresh)

    # --- AIM 4: Spatial Domain Filtering ---
    elif aim == 'aim4':
        avg = cv2.blur(img, (5, 5))
        gauss = cv2.GaussianBlur(img, (5, 5), 0)
        med = cv2.medianBlur(img, 5)
        bilateral = cv2.bilateralFilter(img, 9, 75, 75)

        output_imgs['i) Averaging Filter'] = img_to_base64(avg)
        output_imgs['ii) Gaussian Filter'] = img_to_base64(gauss)
        output_imgs['iii) Median Filter'] = img_to_base64(med)
        output_imgs['iv) Bilateral Filter'] = img_to_base64(bilateral)

    # --- AIM 5: Image Inpainting ---
    elif aim == 'aim5':
        gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
        mask = np.zeros(gray.shape, np.uint8)
        cv2.line(mask, (0, 0), (img.shape[1], img.shape[0]), 255, 5)  # Simulated damage

        telea = cv2.inpaint(img, mask, 3, cv2.INPAINT_TELEA)
        ns = cv2.inpaint(img, mask, 3, cv2.INPAINT_NS)

        output_imgs['Simulated Damage Mask'] = img_to_base64(mask)
        output_imgs['Telea Method Inpainting'] = img_to_base64(telea)
        output_imgs['Navier-Stokes (NS) Method'] = img_to_base64(ns)

    # --- AIM 6: Lossless Compression ---
    elif aim == 'aim6':
        orig_size = os.path.getsize(img_path) / 1024
        _, encoded_png = cv2.imencode('.png', img, [cv2.IMWRITE_PNG_COMPRESSION, 9])
        comp_size = len(encoded_png) / 1024

        info_text = f"Original File Size: {orig_size:.2f} KB | Lossless PNG Compressed Size: {comp_size:.2f} KB"
        output_imgs['Compressed Representation'] = img_to_base64(img)

    # --- AIM 7: Morphological Operations ---
    elif aim == 'aim7':
        gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
        _, binary = cv2.threshold(gray, 127, 255, cv2.THRESH_BINARY)
        kernel = np.ones((5, 5), np.uint8)

        erosion = cv2.erode(binary, kernel, iterations=1)
        dilation = cv2.dilate(binary, kernel, iterations=1)
        opening = cv2.morphologyEx(binary, cv2.MORPH_OPEN, kernel)
        closing = cv2.morphologyEx(binary, cv2.MORPH_CLOSE, kernel)

        output_imgs['Erosion'] = img_to_base64(erosion)
        output_imgs['Dilation'] = img_to_base64(dilation)
        output_imgs['Opening'] = img_to_base64(opening)
        output_imgs['Closing'] = img_to_base64(closing)

    # --- AIM 8: Object Detection using Correlation Principle ---
    elif aim == 'aim8':
        gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
        if file2:
            template_path = os.path.join(UPLOAD_FOLDER, file2.filename)
            file2.save(template_path)
            template = cv2.imread(template_path, 0)

            res = cv2.matchTemplate(gray, template, cv2.TM_CCOEFF_NORMED)
            _, _, _, max_loc = cv2.minMaxLoc(res)

            h, w = template.shape
            top_left = max_loc
            bottom_right = (top_left[0] + w, top_left[1] + h)

            detected_img = img.copy()
            cv2.rectangle(detected_img, top_left, bottom_right, (0, 255, 0), 3)

            output_imgs['Template Image'] = img_to_base64(template)
            output_imgs['Detected Object (Correlation)'] = img_to_base64(detected_img)
        else:
            info_text = "Please upload a 'Template Image' in the 2nd input field to perform correlation object detection."

    # --- AIM 9: Top-Hat Transform for Background Illumination Correction ---
    elif aim == 'aim9':
        gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
        kernel = cv2.getStructuringElement(cv2.MORPH_RECT, (15, 15))
        tophat = cv2.morphologyEx(gray, cv2.MORPH_TOPHAT, kernel)
        enhanced = cv2.add(gray, tophat)

        output_imgs['Original Grayscale'] = img_to_base64(gray)
        output_imgs['Top-Hat Transformation'] = img_to_base64(tophat)
        output_imgs['Illumination Corrected Result'] = img_to_base64(enhanced)

    # --- AIM 10: Colour Space Conversions ---
    elif aim == 'aim10':
        rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
        hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)
        ycrcb = cv2.cvtColor(img, cv2.COLOR_BGR2YCrCb)
        lab = cv2.cvtColor(img, cv2.COLOR_BGR2LAB)

        output_imgs['RGB Format'] = img_to_base64(rgb)
        output_imgs['HSV Space'] = img_to_base64(hsv)
        output_imgs['YCrCb Space'] = img_to_base64(ycrcb)
        output_imgs['Lab Space'] = img_to_base64(lab)

    # --- AIM 11: Edge Detection Methods ---
    elif aim == 'aim11':
        gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
        canny = cv2.Canny(gray, 100, 200)

        sobelx = cv2.Sobel(gray, cv2.CV_64F, 1, 0, ksize=3)
        sobely = cv2.Sobel(gray, cv2.CV_64F, 0, 1, ksize=3)
        sobel = np.uint8(cv2.magnitude(sobelx, sobely))

        kernelx = np.array([[1, 1, 1], [0, 0, 0], [-1, -1, -1]], dtype=int)
        kernely = np.array([[-1, 0, 1], [-1, 0, 1], [-1, 0, 1]], dtype=int)
        prewitt = cv2.filter2D(gray, -1, kernelx) + cv2.filter2D(gray, -1, kernely)

        output_imgs['Canny Detector'] = img_to_base64(canny)
        output_imgs['Sobel Detector'] = img_to_base64(sobel)
        output_imgs['Prewitt Detector'] = img_to_base64(prewitt)

    return jsonify({'images': output_imgs, 'info': info_text})


if __name__ == '__main__':
    print("Application live at: http://127.0.0.1:5000")
    app.run(debug=True)
