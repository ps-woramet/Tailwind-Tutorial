-css framework
เครื่องมือที่ช่วยนักพัฒนาออกแบบเว็บไซต์ได้ง่ายและรวดเร็วขึ้น

-หน้าที่ 
จัดเตรียมวางโครงสร้างหน้าเว็บขั้นพื้นฐานเอาไว้ ให้ผู้พัฒนาสามารถเลือกปรับแต่งได้ตามความต้องการ

-ข้อดี
ลดเวลาการออกแบบเว็บไซต์
ลดโอกาสข้อผิดพลาด responsive

-Tailwind css
คือ Utility-First Css framework ที่ช่วยให้สามารถออกแบบเว็บได้อย่างรวดเร็ว เนื่องจากมี class สำเร็จรูปที่สามารถใช้งานได้ทันทีโดยไม่จำเป็นต้องเขียน css ได้โดยตรง

-Utility-First Css framework
เป็นการจัดการโดยตรงกับ element ที่เป็น class ย่อยๆและนำมาประกอบกันในภายหลังและเพื่อความสะดวกในการใช้งาน clas ย่อยๆ
ซ้ำกันใน Tailwind css จะใช้คำสั่ง @apply เพื่อรวม class และ สร้าง class ให้ผู้พัฒนาสามารถเลือกปรับแต่งได้ตามความต้องการ

Tailwind Diractives
@tailwind base; จัดการ element(tag)
@tailwind components; จัดการ class
@tailwind utilities; จัดการ ปรับแต่งตัว class


1. ติดตั้ง tailwind
    npm install -D tailwindcss

2. สร้าง tailwind.config.js file
    npx tailwindcss init

3. Configure your template paths ตั้งค่า paths ของ template file ใน tailwind.configs.js
    module.exports = {
    content: ["./src/**/*.{html,js}"],
    theme: {
        extend: {},
    },
    plugins: [],
    }

4. เพิ่ม directives ที่ src > input.css 
    @tailwind base;
    @tailwind components;
    @tailwind utilities;

5. แปลง directives(@tailwind base;@tailwind components;@tailwind utilities;) เป็นไฟล์นามสกุล .css ต้องใช้หากต้องการเปลี่ยนแปลงค่า
    npx tailwindcss -i ./src/input.css -o ./dist/output.css --watch

6. src > index.html
    <!doctype html>
    <html>
    <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link href="../dist/output.css" rel="stylesheet">
    </head>
    <body>
    <h1 class="text-3xl font-bold underline">
        Hello world!
    </h1>
    </body>
    </html>

7. package.json เพิ่ม scripts เพื่อจะให้ run ง่ายๆ (npm run build)

    {
        "devDependencies": {
            "tailwindcss": "^3.3.3"
        },
        "scripts": {
            "build" : "npx tailwindcss -i ./src/input.css -o ./dist/output.css --watch"
        }
    }

8. Layer and apply

    tailwind css คือ Utitlity-first css framwork เป็นการจัดการโดยตรงกับ element ที่เป็น class ย่อยๆและนำมาประกอบกันในภายหลังและเพื่อความสะดวกในการใช้งาน
    และเพื่อความสะดวกในการใช้งาน class ย่อยๆซ้ำกันภายใน tailwind css จะใช้คำสั่ง "@apply" เพื่อรวม class และสร้าง class ใหม่
    
    @tailwind base; จัดการ element
    @taliwind components; จัดการ class
    @tailwind utilities; ปรับแต่ง class

    ตัวอย่าง  หากต้องการให้ tag a เป็นสีเขียวความเข้ม 500
        <a href = "#">Menu 1</a>
        <a href = "#">Menu 2</a>
        <a href = "#">Menu 3</a>

        แก้ไข input.css

        @layer base{
            a{
                @apply text-green-500;
            }
        }

    ตัวอย่าง  หากต้องการให้ clas menu-button มีค่าพื้นหลังแดง ตัวหนังสือสีขาว
        <a href="#" class="menu-button">Menu 3 layer components</a>
        <a href="#" class="menu-button">Menu 4 layer components</a>

        แก้ไข input.css
        
        @layer components{
            .menu-button{
                @apply text-white bg-red-500 p-0.5
            }
        }
    
    ตัวอย่าง หากต้องการให้ class text-gray-500 ตัวอักษรเป็นสีน้ำเงิน

        แก้ไข input.css
        
        @layer utilities{
            .text-gray-500{
                color: blue;
            }
        }