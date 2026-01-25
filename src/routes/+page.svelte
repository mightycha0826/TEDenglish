<script lang="ts">
    import { onMount } from "svelte";
    import C1 from "$lib/assets/images/TEDC1.jpg";
    import C2 from "$lib/assets/images/TEDC2.jpg";
    import C3 from "$lib/assets/images/TEDC3.jpg";
    import S1 from "$lib/assets/images/TED1.jpg";
    import S2 from "$lib/assets/images/TED2.jpg";
    import S3 from "$lib/assets/images/TED3.jpg";
    import mapImage from "$lib/assets/images/TEDMAP.jpg";
    import TEDS1 from "$lib/assets/images/TEDS1.jpg";
    import TEDS2 from "$lib/assets/images/TEDS2.jpg";
    import TEDS3 from "$lib/assets/images/TEDS3.jpg";
    import TEDS4 from "$lib/assets/images/TEDS4.jpg";
    import TEDa from "$lib/assets/images/TEDa.jpg";
    import TEDb from "$lib/assets/images/TEDb.jpg";
    import TEDc from "$lib/assets/images/TEDc.jpg";

    let currentSlide = 0;
    const slides = [
        {
            image: S1,
            title: "미래를 여는 교육",
            subtitle: "FUTURE EDUCATION ACADEMY",
        },
        {
            image: S2,
            title: "최고의 교육 환경",
            subtitle: "BEST LEARNING ENVIRONMENT",
        },
        {
            image: S3,
            title: "입시영어는 테드",
            subtitle: "MAKE YOUR DREAMS COME TRUE",
        },
    ];

    const features = [
        {
            image: C1,
            title: "체계적인 커리큘럼",
            description: "암튼 무언가 엄청난 자기주도성을 길러줍니다.",
        },
        {
            image: C2,
            title: "우와수업자료",
            description: "테드 자체 교재가 무척이나 대단합니다.",
        },
        {
            image: C3,
            title: "검증된 성과",
            description: "진짜로 성적이 팍팍 오르는 게 눈에 보입니다.",
        },
    ];

    // YouTube video information
    const youtubeVideo = {
        url: "https://youtu.be/ravdYvqJhlc",
        videoId: "ravdYvqJhlc",
        thumbnail: "https://img.youtube.com/vi/ravdYvqJhlc/maxresdefault.jpg",
        title: "학원 소개 영상",
    };

    const programs = [
        {
            title: "정규 수업 과정",
            description:
                "주요 과목의 기초부터 심화까지 단계별로 체계적인 학습을 진행합니다. 소수정예 수업으로 집중도 높은 학습 환경을 제공합니다.",
            image: TEDa,
        },
        {
            title: "특별 집중 과정",
            description:
                "부족한 과목을 집중적으로 보완하거나 우수한 과목을 더욱 발전시킬 수 있는 맞춤형 특별 프로그램입니다.",
            image: TEDb,
        },
        {
            title: "입시 대비 과정",
            description:
                "대학 입시를 준비하는 학생들을 위한 전문 프로그램으로 수시와 정시 전략부터 실전 대비까지 완벽하게 준비합니다.",
            image: TEDc,
        },
    ];

    const admissionInfo = {
        targets: [
            "초등부 1학년 ~ 6학년",
            "중등부 1학년 ~ 3학년",
            "고등부 1학년 ~ 3학년",
        ],
        process: [
            "상담 신청 (전화 또는 방문)",
            "학력 진단 테스트 실시",
            "레벨별 반 배정",
            "수강 등록 및 수업 시작",
        ],
        documents: [
            "입학원서 1부",
            "최근 성적표 사본 1부",
            "학생 증명사진 2매",
        ],
    };

    const contactInfo = [
        {
            title: "주소",
            content: "천안시 서북구 불당 34길 25-4 4F 401호",
        },
        {
            title: "문의",
            content: "대표번호: 041-415-0703",
        },
    ];

    const newsData = [
        {
            id: 1,
            title: "2026학년도 수능 영어 분석 설명회",
            date: "2026.01.15",
            href: "https://blog.naver.com/tedenglish_1/224078902006",
            image: TEDS1,
        },
        {
            id: 2,
            title: "겨울방학 특강 개강 안내",
            date: "2025.12.20",
            image: TEDS2,
        },
        {
            id: 3,
            title: "TED 잉글리시 우수 장학생 명단 발표",
            date: "2025.12.10",
            image: TEDS3,
        },
        {
            id: 4,
            title: "예비 중1, 고1 입시 전략 설명회",
            date: "2025.11.25",
            image: TEDS4,
        },
    ];

    let interval: ReturnType<typeof setInterval>;

    const startSlideShow = () => {
        stopSlideShow();
        interval = setInterval(() => {
            currentSlide = (currentSlide + 1) % slides.length;
        }, 5000);
    };

    const stopSlideShow = () => {
        if (interval) clearInterval(interval);
    };

    onMount(() => {
        startSlideShow();
        return stopSlideShow;
    });

    function goToSlide(index: number) {
        currentSlide = index;
        startSlideShow(); // Reset timer when manually changing slides
    }

    function scrollToSection(sectionId: string) {
        const element = document.getElementById(sectionId);
        if (element) {
            element.scrollIntoView({ behavior: "smooth" });
        }
    }
</script>

<!-- 메인 슬라이더 -->
<section id="home" class="hero-slider">
    {#each slides as slide, index}
        <div class="slide" class:active={currentSlide === index}>
            <img src={slide.image} alt={slide.title} />
            <div class="slide-overlay">
                <h1 class="slide-title">{slide.title}</h1>
                <p class="slide-subtitle">{slide.subtitle}</p>
            </div>
        </div>
    {/each}

    <div class="slider-controls">
        {#each slides as _, index}
            <button
                class="slider-dot"
                class:active={currentSlide === index}
                on:click={() => goToSlide(index)}
                aria-label="슬라이드 {index + 1}"
            ></button>
        {/each}
    </div>

    <button class="scroll-indicator" on:click={() => scrollToSection("about")}>
        <span class="scroll-text">SCROLL DOWN</span>
        <span class="scroll-arrow">↓</span>
    </button>
</section>

<!-- 학원소개 섹션 -->
<section id="about" class="intro-section">
    <h2 class="section-title">학원 특징</h2>
    <div class="intro-slider">
        {#each features as feature}
            <div class="intro-card">
                <div
                    class="card-image"
                    style="background-image: url({feature.image})"
                ></div>
                <div class="card-content">
                    <h3 class="card-title">{feature.title}</h3>
                    <p class="card-description">{feature.description}</p>
                </div>
            </div>
        {/each}
    </div>

    <!-- YouTube 소개 영상 -->
    <div class="video-section">
        <h3 class="video-title">학원 소개 영상</h3>
        <div class="video-container">
            <iframe
                src="https://www.youtube.com/embed/{youtubeVideo.videoId}"
                title={youtubeVideo.title}
                frameborder="0"
                allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
                allowfullscreen
            ></iframe>
        </div>
    </div>
</section>

<!-- 교육과정 섹션 -->
<section id="programs" class="program-section">
    <div class="program-container">
        <h2 class="section-title">주요 프로그램</h2>
        <div class="program-slider">
            {#each programs as program}
                <div class="program-card">
                    <div
                        class="program-image"
                        style="background-image: url({program.image})"
                    ></div>
                    <div class="program-content">
                        <h3 class="program-title">{program.title}</h3>
                        <p class="program-description">{program.description}</p>
                    </div>
                </div>
            {/each}
        </div>

        <div class="news-section">
            <div class="news-header">
                <h3 class="news-title">TED 뉴스</h3>
                <button
                    class="view-more-btn"
                    on:click={() => scrollToSection("news-list")}
                    aria-label="뉴스 더보기"
                >
                    +
                </button>
            </div>
            <div class="news-slider">
                {#each newsData as news}
                    <a
                        href={news.href || "#"}
                        class="news-card"
                        target="_blank"
                        rel="noopener noreferrer"
                    >
                        <div
                            class="news-image"
                            style="background-image: url({news.image})"
                        ></div>
                        <div class="news-content">
                            <span class="news-date">{news.date}</span>
                            <h4 class="news-item-title">{news.title}</h4>
                        </div>
                    </a>
                {/each}
            </div>
        </div>
    </div>
</section>

<!-- 입학안내 섹션 -->
<section id="admissions" class="admissions-content">
    <h2 class="section-title">입학 안내</h2>

    <div class="info-box">
        <h3>모집 대상</h3>
        <ul>
            {#each admissionInfo.targets as target}
                <li>{target}</li>
            {/each}
        </ul>
    </div>

    <div class="info-box">
        <h3>입학 절차</h3>
        <ul>
            {#each admissionInfo.process as step}
                <li>{step}</li>
            {/each}
        </ul>
    </div>

    <div class="info-box">
        <h3>문의 및 상담</h3>
        <p>전화: 041-4150-0703</p>
        <p>운영시간: 평일 오전 9시 - 오후 10시, 토요일 오전 9시 - 오후 6시</p>
        <p>상담은 예약제로 운영되며, 사전 예약 후 방문해주시기 바랍니다.</p>
    </div>
</section>

<!-- 오시는길 섹션 -->
<section id="contact" class="contact-content">
    <h2 class="section-title">오시는 길</h2>

    <div class="contact-grid">
        {#each contactInfo as info}
            <div class="contact-card">
                <h3>{info.title}</h3>
                <p>{@html info.content}</p>
            </div>
        {/each}
    </div>

    <div class="map-container">
        <div class="map-placeholder" style="background-image: url({mapImage})">
            <div class="map-info">
                <h4>TED 잉글리시</h4>
                <p>충남 천안시 서북구 불당34길 25-4</p>
                <a
                    href="https://map.naver.com/v5/search/%EC%B6%A9%EB%82%A8%20%EC%B2%9C%EC%95%88%EC%8B%9C%20%EC%84%9C%EB%B6%81%EA%B5%AC%20%EB%B6%88%EB%8B%B934%EA%B8%B8%2025-4"
                    target="_blank"
                    rel="noopener noreferrer"
                    class="map-button"
                >
                    네이버 지도로 보기
                </a>
            </div>
        </div>
    </div>
</section>

<style>
    /* 메인 슬라이더 */
    .hero-slider {
        position: relative;
        width: 100%;
        height: 100vh;
        overflow: hidden;
    }

    .slide {
        position: absolute;
        width: 100%;
        height: 100%;
        opacity: 0;
        transition: opacity 1.5s ease-in-out;
    }

    .slide.active {
        opacity: 1;
    }

    .slide img {
        width: 100%;
        height: 100%;
        object-fit: cover;
    }

    .slide-overlay {
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        background: rgba(0, 0, 0, 0.3);
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        color: white;
    }

    .slide-title {
        font-size: 56px;
        font-weight: 700;
        margin-bottom: 20px;
        opacity: 0;
        transform: translateY(30px);
        animation: fadeInUp 1s forwards 0.3s;
    }

    .slide-subtitle {
        font-size: 24px;
        font-weight: 300;
        opacity: 0;
        transform: translateY(30px);
        animation: fadeInUp 1s forwards 0.6s;
    }

    @keyframes fadeInUp {
        to {
            opacity: 1;
            transform: translateY(0);
        }
    }

    .slider-controls {
        position: absolute;
        bottom: 40px;
        left: 50%;
        transform: translateX(-50%);
        display: flex;
        gap: 15px;
        z-index: 10;
    }

    .slider-dot {
        width: 12px;
        height: 12px;
        border-radius: 50%;
        background: rgba(255, 255, 255, 0.5);
        border: none;
        cursor: pointer;
        transition: all 0.3s;
        padding: 0;
    }

    .slider-dot.active {
        background: white;
        width: 40px;
        border-radius: 6px;
    }

    .scroll-indicator {
        position: absolute;
        bottom: 100px;
        left: 50%;
        transform: translateX(-50%);
        display: flex;
        flex-direction: column;
        align-items: center;
        color: white;
        animation: bounce 2s infinite;
        background: none;
        border: none;
        cursor: pointer;
    }

    @keyframes bounce {
        0%,
        20%,
        50%,
        80%,
        100% {
            transform: translateX(-50%) translateY(0);
        }
        40% {
            transform: translateX(-50%) translateY(-10px);
        }
        60% {
            transform: translateX(-50%) translateY(-5px);
        }
    }

    .scroll-text {
        font-size: 14px;
        margin-bottom: 10px;
        letter-spacing: 2px;
    }

    .scroll-arrow {
        font-size: 24px;
    }

    /* 학원소개 섹션 */
    .intro-section {
        max-width: 1200px;
        margin: 0 auto;
        padding: 100px 40px;
    }

    .section-title {
        font-size: 42px;
        font-weight: 700;
        text-align: center;
        margin-bottom: 60px;
        color: #2c3e50;
    }

    .intro-card {
        text-align: left;
        padding: 0;
        background: white;
        border-radius: 15px;
        overflow: hidden;
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
        transition: box-shadow 0.3s;
        height: 100%;
        display: flex;
        flex-direction: column;
        flex: 0 0 300px;
    }

    .intro-card:hover {
        box-shadow: 0 15px 40px rgba(0, 0, 0, 0.1);
    }

    .card-image {
        width: 100%;
        height: 300px; /* Increased vertical height */
        background-size: cover;
        background-position: center;
        transition: transform 0.3s ease;
    }

    .intro-card:hover .card-image {
        transform: scale(1.05);
    }

    .card-content {
        padding: 30px;
        flex-grow: 1;
    }

    .card-title {
        font-size: 24px;
        font-weight: 700;
        margin-bottom: 15px;
        color: #2c3e50;
    }

    .card-description {
        font-size: 16px;
        color: #666;
        line-height: 1.6;
    }

    /* YouTube 비디오 섹션 */
    .video-section {
        margin-top: 80px;
        text-align: center;
    }

    .video-title {
        font-size: 35px;
        font-weight: 700;
        margin-bottom: 40px;
        color: #2c3e50;
    }

    .video-container {
        position: relative;
        width: 100%;
        max-width: 1000px;
        margin: 0 auto;
        padding-bottom: 56.25%; /* 16:9 aspect ratio */
        height: 0;
        overflow: hidden;
        border-radius: 15px;
        box-shadow: 0 10px 40px rgba(0, 0, 0, 0.15);
    }

    .video-container iframe {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        border-radius: 15px;
    }

    /* 교육과정 섹션 */
    .program-section {
        background: #f8f9fa;
        padding: 100px 40px;
    }

    .program-container {
        max-width: 1200px;
        margin: 0 auto;
    }

    .program-card {
        background: white;
        border-radius: 10px;
        overflow: hidden;
        box-shadow: 0 5px 15px rgba(0, 0, 0, 0.08);
        transition: box-shadow 0.3s;
        flex: 0 0 350px;
    }

    .program-card:hover {
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
    }

    .program-image {
        width: 100%;
        height: 250px;
        background: #ddd;
        display: flex;
        align-items: center;
        justify-content: center;
        color: #999;
        font-size: 18px;
        transition: transform 0.3s ease;
    }

    .program-card:hover .program-image {
        transform: scale(1.05);
    }

    .program-content {
        padding: 30px;
    }

    .program-title {
        font-size: 22px;
        font-weight: 600;
        margin-bottom: 15px;
        color: #2c3e50;
    }

    .program-description {
        font-size: 15px;
        color: #666;
        line-height: 1.7;
    }

    /* 뉴스 섹션 */
    .news-section {
        margin-top: 80px;
    }

    .news-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 30px;
        padding-left: 10px;
        border-left: 5px solid #3498db;
    }

    .news-title {
        font-size: 28px;
        font-weight: 700;
        color: #2c3e50;
        margin-bottom: 0;
        padding-left: 0;
        border-left: none;
    }

    .view-more-btn {
        background: none;
        border: none;
        font-size: 32px;
        color: #95a5a6;
        cursor: pointer;
        padding: 0 10px;
        line-height: 1;
        transition: color 0.3s;
    }

    .view-more-btn:hover {
        color: #2c3e50;
    }

    .news-slider {
        display: flex;
        overflow-x: auto;
        gap: 20px;
        padding-bottom: 20px;
        -webkit-overflow-scrolling: touch;
        scroll-behavior: smooth;
        scrollbar-width: none; /* Firefox */
        -ms-overflow-style: none; /* IE and Edge */
    }

    .news-slider::-webkit-scrollbar {
        display: none; /* Chrome, Safari, Opera */
    }

    .news-slider::-webkit-scrollbar-thumb {
        background: #bdc3c7;
        border-radius: 4px;
    }

    .news-slider::-webkit-scrollbar-thumb:hover {
        background: #95a5a6;
    }

    .intro-slider {
        display: flex;
        overflow-x: auto;
        gap: 20px;
        padding-bottom: 20px;
        -webkit-overflow-scrolling: touch;
        scroll-behavior: smooth;
        scrollbar-width: none; /* Firefox */
        -ms-overflow-style: none; /* IE and Edge */
    }

    .intro-slider::-webkit-scrollbar {
        display: none; /* Chrome, Safari, Opera */
    }

    .intro-slider::-webkit-scrollbar-thumb {
        background: #bdc3c7;
        border-radius: 4px;
    }

    .intro-slider::-webkit-scrollbar-thumb:hover {
        background: #95a5a6;
    }

    .program-slider {
        display: flex;
        overflow-x: auto;
        gap: 20px;
        padding-bottom: 20px;
        -webkit-overflow-scrolling: touch;
        scroll-behavior: smooth;
        scrollbar-width: none; /* Firefox */
        -ms-overflow-style: none; /* IE and Edge */
    }

    .program-slider::-webkit-scrollbar {
        display: none; /* Chrome, Safari, Opera */
    }

    .program-slider::-webkit-scrollbar-thumb {
        background: #bdc3c7;
        border-radius: 4px;
    }

    .program-slider::-webkit-scrollbar-thumb:hover {
        background: #95a5a6;
    }

    .news-card {
        flex: 0 0 300px;
        background: white;
        border-radius: 10px;
        overflow: hidden;
        box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        transition: box-shadow 0.3s;
        cursor: pointer;
        text-decoration: none;
        display: block;
    }

    .news-card:hover {
        box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
    }

    .news-image {
        height: 180px;
        background-size: cover;
        background-position: center;
        background-color: #eee;
        transition: transform 0.3s ease;
    }

    .news-card:hover .news-image {
        transform: scale(1.05);
    }

    .news-content {
        padding: 20px;
    }

    .news-date {
        font-size: 13px;
        color: #95a5a6;
        display: block;
        margin-bottom: 8px;
    }

    .news-item-title {
        font-size: 16px;
        font-weight: 600;
        color: #2c3e50;
        line-height: 1.5;
        margin: 0;
    }

    /* 입학안내 섹션 */
    .admissions-content {
        max-width: 1200px;
        margin: 0 auto;
        padding: 100px 40px;
    }

    .info-box h3 {
        font-size: 28px;
        color: #2c3e50;
        margin-bottom: 20px;
        padding-bottom: 15px;
        border-bottom: 2px solid #3498db;
    }

    .info-box p {
        font-size: 16px;
        line-height: 1.8;
        color: #666;
        margin-bottom: 15px;
    }

    .info-box ul {
        list-style: none;
        padding-left: 0;
    }

    .info-box li {
        padding: 12px 0;
        border-bottom: 1px solid #f0f0f0;
        font-size: 16px;
        color: #555;
    }

    .info-box li:before {
        content: "✓ ";
        color: #3498db;
        font-weight: bold;
        margin-right: 10px;
    }

    /* 오시는길 섹션 */
    .contact-content {
        max-width: 1200px;
        margin: 0 auto;
        padding: 100px 40px;
    }

    .contact-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        gap: 40px;
        margin-bottom: 40px;
    }

    .contact-card {
        background: #f8f9fa;
        padding: 30px;
        border-radius: 10px;
    }

    .contact-card h3 {
        font-size: 22px;
        color: #2c3e50;
        margin-bottom: 20px;
    }

    .contact-card p {
        font-size: 16px;
        line-height: 1.8;
        color: #666;
    }

    .map-container {
        width: 100%;
        height: 400px;
        border-radius: 10px;
        overflow: hidden;
        margin-bottom: 20px;
    }

    .map-placeholder {
        width: 100%;
        height: 100%;
        background-size: cover;
        background-position: center;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .map-info {
        background: white;
        padding: 40px;
        border-radius: 10px;
        text-align: center;
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
        max-width: 400px;
        width: 90%;
    }

    .map-info h4 {
        font-size: 24px;
        color: #2c3e50;
        margin-bottom: 10px;
    }

    .map-info p {
        color: #666;
        margin-bottom: 25px;
        font-size: 16px;
    }

    .map-button {
        display: inline-block;
        background: #03c75a; /* Naver Green */
        color: white;
        padding: 12px 30px;
        border-radius: 5px;
        text-decoration: none;
        font-weight: 700;
        transition: background 0.3s;
    }

    .map-button:hover {
        background: #02b351;
    }

    @media (max-width: 768px) {
        .slide-title {
            font-size: 36px;
        }

        .slide-subtitle {
            font-size: 18px;
        }

        .section-title {
            font-size: 32px;
        }
    }
</style>
