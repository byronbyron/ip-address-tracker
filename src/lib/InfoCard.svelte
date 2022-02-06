<div>
    <ul>
        <li>
            <span>IP Address</span>
            <strong>192.212.174.101</strong>
        </li>

        <li>
            <span>Location</span>
            <strong>Brooklyn, NY 10001</strong>
        </li>

        <!-- add offset value dynamically using the API -->
        <li>
            <span>Timezone</span>
            <strong>UTC -05:00</strong>
        </li>
        
        <li>
            <span>ISP</span>
            <strong>SpaceX Starlink</strong>
        </li>
    </ul>
</div>

<style>
    div {
        padding: 1.625rem;
        background-color: white;
        border-radius: 0.9375rem;
        text-align: center;
    }

    ul {
        margin: 0;
        padding: 0;
        list-style: none;
    }

    span {
        font-size: 11px;
        font-weight: 700;
        line-height: 1.2;
        display: block;
        text-transform: uppercase;
        color: var(--dark-gray);
        margin-bottom: 0.4375rem;
        letter-spacing: 0.05em;
    }

    strong {
        font-size: 1.25rem;
        font-weight: 500;
        display: block;
        margin-bottom: 1.5rem;
    }

    li:last-child strong {
        margin-bottom: 0;
    }

    @media (min-width: 992px) {
        div {
            max-width: 1110px;
            margin-left: auto;
            margin-right: auto;
            padding: 0;
        }

        ul {
            display: flex;
        }

        li {
            padding: 2.25rem 3rem 2.25rem 2rem;
            flex: 1;
            text-align: left;
            position: relative;
        }

        li::after {
            content: '';
            display: block;
            width: 1px;
            height: 4.75rem;
            background-color: hsl(0 0% 0% / 0.15);
            position: absolute;
            top: 50%;
            right: 0;
            transform: translateY(-50%);
        }

        span {
            font-size: 13px;
            letter-spacing: 0.1em;
            margin-bottom: 0.875rem;
        }

        strong {
            font-size: 1.625rem;
            margin-bottom: 0;
        }
    }
</style>
