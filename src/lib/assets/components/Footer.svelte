<script lang="ts">
    function scrollToSection(sectionId: string, event: Event) {
        event.preventDefault();
        const element = document.getElementById(sectionId);
        if (element) {
            element.scrollIntoView({ behavior: "smooth" });
        }
    }
</script>

<footer>
    <div class="footer-content">
        <div class="footer-section">
            <h3>TED 잉글리시</h3>
            <p>주소: 충남 천안시 서북구 불당34길 25-4 401호</p>
            <p>입학상담: 0507-1496-0708</p>
            <p>
                <a
                    href="https://place.map.kakao.com/1300721845#photoList?type=all&pidx=0&t_src=kakaotalk&t_ch=talkchannel&t_obj=placedetail"
                    target="_blank"
                    rel="noopener noreferrer"
                >
                    카카오톡 문의
                </a>
            </p>
            <p>
                <a
                    href="https://blog.naver.com/tedenglish_1"
                    target="_blank"
                    rel="noopener noreferrer"
                >
                    네이버 블로그
                </a>
            </p>
        </div>
        <div class="footer-section">
            <h3>운영 시간</h3>
            <p>평일: 오전 9시 - 오후 10시</p>
            <p>토요일: 오전 9시 - 오후 6시</p>
            <p>일요일 및 공휴일 휴무</p>
        </div>
    </div>
    <div class="footer-bottom">
        <p>Copyright © 2026 TED잉글리시. All rights reserved.</p>
    </div>
</footer>

<style>
    footer {
        background: #2c3e50;
        color: white;
        padding: 60px 40px 30px;
    }

    .footer-content {
        max-width: 1200px;
        margin: 0 auto;
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        gap: 40px;
        margin-bottom: 40px;
    }

    .footer-section h3 {
        font-size: 18px;
        margin-bottom: 20px;
    }

    .footer-section p,
    .footer-section a {
        font-size: 14px;
        color: #bdc3c7;
        line-height: 2;
        text-decoration: none;
    }

    .footer-section a:hover {
        color: white;
    }

    .footer-bottom {
        text-align: center;
        padding-top: 30px;
        border-top: 1px solid #34495e;
        color: #95a5a6;
        font-size: 14px;
    }
    @media (max-width: 768px) {
        footer {
            padding: 40px 20px 20px;
        }
    }
</style>
